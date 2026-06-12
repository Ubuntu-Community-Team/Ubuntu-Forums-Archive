---
title: "Can't get temp info on my LCD using LCDd &amp; lcdproc"
date: 2009-02-08
forum: Hardware
---

### Post by quazar on 2009-02-08
I have a working 2x16 LCD in my computer case (HD44780 running LCDd and lcdproc).
I would like this display to show the temperature readings of both my CPU and motherboard. I found a perl script to display temperature readings on this LCD, but my problem is that the script expects all temperature data can be found at the same location, whereas the temperature sensor for the CPU is located at:
/sys/bus/pci/drivers/k8temp/0000:00:18.3
and the motherboard sensor is located at:
/sys/devices/platform/it87.552

How can I adjust this script to get both CPU and motherboard readings on my LCD?
I have tried 
my $chip='/sys/bus/pci/drivers/k8temp/0000:00:18.3' & '/sys/devices/platform/it87.552'
and:
my $chip='/sys/bus/pci/drivers/k8temp/0000:00:18.3'
my $chip='/sys/devices/platform/it87.552'

Both don't work. I'm sorry, I'm a Perl nOOb

```
#!/usr/bin/perl
########################################################################
## This is a perl script that outputs some data coming                ##
## from lm-sensors to an LCD.                                         ##
##                                                                    ##
## This script needs a working version of lm-sensors                  ##
## (see http://www2.lm-sensors.nu/~lm78/ for more details)            ##
## You need to change some variables below.                           ##
##                                                                    ##
## This script needs a working version of LCDd, the                   ##
## server daemon coming with the package lcdproc.                     ##
## (see http://lcdproc.omnipotent.net/ for more details)              ##
##                                                                    ##
## This script is optimized for 16x2, 20x2, 20x4 displays. It         ##
## will also output on different sized displays but that won't        ##
## look very nice. (A lot of waste). 40x2 or 40x4 are still           ##
## acceptable. If you have a different sized display, you should      ##
## change where the widgets are placed on the sreen.                  ##
## (http://lcdproc.omnipotent.net/netstuff.txt for more details)      ##
##                                                                    ##
## Also check out https://nederwiet.wox.org/www/sensors-lcd/          ##
## A similar project where I found some inspiration.                  ##
##                                                                    ##
## See the README for more details.                                   ##
##                                                                    ##
## The author:                                                        ## 
## Nick Van Helleputte, Belgium                                       ##
## May 2002                                                           ##
########################################################################

## --> CHANGE THESE VARIABLES !!!!!!
## variables regarding lm_sensors, update these conform to your system
my $chip='/sys/bus/pci/drivers/k8temp/0000:00:18.3'  # directory where lm_sensors writes its data
#my $chip='/sys/devices/platform/it87.552'
my $cpusens='temp1_input';  # cpu sensor, in my case temp3
my $syssens='temp2';  # mobo sensor, in my case temp2
my $fan1sens='fan1';  # cpufan sensor
my $fan2sens='fan2';  # casefan sensor

## variables regarding LCDd, update if necessary, but normally these are correct
my $server='localhost';
my $port='13666';

########################################################################
##                                                                    ##
## don't change the following unless you know what you're doing       ##
##                                                                    ##
########################################################################

## Check if the values above are correct
if (!-d "$chip") { 
    print "$chip not found! \n";
    print "Did you change the variables? Edit this file please.\n";
    exit 0;
}
if (!-e "$chip/$cpusens") {
    print "No cpu sensor found! \n";
    print "Did you change the variables? Edit this file please.\n";
    exit 0;
}

if (!-e "$chip/$syssens") {
    print "No system sensor found! \n";
    print "Did you change the variables? Edit this file please.\n";
    exit 0;
}

if (!-e "$chip/$fan1sens") {
    print "No cpufan sensor found! \n";
    print "Did you change the variables? Edit this file please.\n";
    exit 0;
}

if (!-e "$chip/$fan2sens") {
    print "No casefan sensor found! \n";
    print "Did you change the variables? Edit this file please.\n";
    exit 0;
}

## don't change these variables
my $cpumin;          # minimal cpu temperature as found in $cpusens
my $cpumax;          # maximal cpu temperature as found in $cpusens
my $sysmin;          # minimal system temperature as found in $syssens
my $sysmax;          # maximal system temperature as found in $syssens
my $cput;            # current cpu temperature
my $syst;            # current system temperature
my $rpm1;            # current speed of cpu fan
my $rpm2;            # current speed of casefan
my $dim1;            # dimension of cpubar
my $dim2;            # dimension of system bar
my $temp;            # temp variabele used for several purposes
my @veld;            # temp array
my $lcdwid;          # width of the lcd
my $lcdhgt;          # height of the lcd
my $title;           # title
my $pos;             # where the temps will be placed
my $maxdim;          # maximum allowable dimension of the bars
my $version='0.96';

use IO::Socket;
use Fcntl;
use Getopt::Std;
use strict;
use vars qw($opt_h $opt_v);


## evaluate the options
&getopts("hv")||die "ERROR: Illegal option. -h for help\n";
&help if ($opt_h);
if($opt_v) {
    print ("LCDsensors $version\n");
    exit 0;
}


## determine minimum and maximum temperatures
$cpumax = getVal( "$chip/$cpusens" , 0 );
$cpumin = getVal( "$chip/$cpusens" , 1 );

# do the same for the system temp
$sysmax = getVal( "$chip/$syssens" , 0 );
$sysmin = getVal( "$chip/$syssens" , 1 );


## create a titel
$_ = `hostname`;
chomp($title = "LCDsensors running on $_");


## Connect to the server
my $remote = IO::Socket::INET->new(
		Proto     => "tcp",
		PeerAddr  => $server,
		PeerPort  => $port,
	)
	|| die "Cannot connect to LCDproc at $server on port $port\n";

$remote->autoflush(1);       # Make sure our messages get there right away
sleep 1;	             # Give server plenty of time to notice us...
print $remote "hello\n";     # tell the server we're here
$temp = <$remote>;           # read the server's answer
@veld = split(/ /,$temp);    # split up the contents
$lcdwid=$veld[7];            # read the lcd's dimensions
$lcdhgt=$veld[9];

# Turn off blocking mode...
fcntl($remote, F_SETFL, O_NONBLOCK);

## define where the widgets will be placed
$pos = $lcdwid - 2;              # temps will be placed next to right edge
$maxdim = 5 * ( $lcdwid - 8 );   # max ($lcdwid - 8) characters for the bars


## do folowing if an LCD with 2 lines is attached
if ($lcdhgt eq '2' ) {

    # Set up some screen widgets
    print $remote "client_set name {Sensors}\n";                   # tell the server our name
    print $remote "screen_add sensor\n";                           # add a sensor screen
    print $remote "widget_add sensor cpu string\n";                # add the cpu string
    print $remote "widget_add sensor ctemp string\n";              # add the string holding the cpu temp
    print $remote "widget_add sensor sys string\n";                # add the sys string
    print $remote "widget_add sensor stemp string\n";              # add the string holding the sys temp
    print $remote "widget_add sensor alarm1 string\n";             # add the string indicating an alarm state
    print $remote "widget_add sensor alarm2 string\n";             # add the string indicating an alarm state
    print $remote "widget_add sensor bar1 hbar\n";                 # add the bar for the cpu temp
    print $remote "widget_add sensor bar2 hbar\n";                 # add the bar for the sys temp
    print $remote "widget_set sensor cpu 1 1 {CPU:}\n";            # put 'CPU:' on the screen
    print $remote "widget_set sensor sys 1 2 {MB:}\n";             # put 'MB:' on the screen

    print $remote "screen_add fans\n";                             # add a fan screen
    print $remote "widget_add fans fan1 string\n";                 # add the fan1 string
    print $remote "widget_add fans rpm1 string\n";                 # add the string holding the fan1 speed
    print $remote "widget_add fans fan2 string\n";                 # add the fan2 string
    print $remote "widget_add fans rpm2 string\n";                 # add the string holding the fan2 speed
    print $remote "widget_set fans fan1 1 1 {Fan1:       rpm}\n";  # put some things on the screen
    print $remote "widget_set fans fan2 1 2 {Fan2:       rpm}\n";

    # do forever
    while(1) {

	chomp($cput = getVal ( "$chip/$cpusens" , 2 ));               # read the cpu temp
	chomp($syst = getVal ( "$chip/$syssens" , 2 ));               # read the system temp
	print $remote "widget_set sensor ctemp $pos 1 {$cput}\n";     # display the current temperatures
	print $remote "widget_set sensor stemp $pos 2 {$syst}\n";
	if ( $cput > $cpumax || $cput < $cpumin ) {                   # check if the temp is within range
	    print $remote "widget_set sensor alarm1 6 1 {ALARM!}\n";  # if not print ALARM
	    $dim1 = 0;                                                # set the bar's dimension to 0
	} else {
	    print $remote "widget_set sensor alarm1 6 1 {}\n";        # clear the ALARM
	    $dim1 = ($cput - $cpumin )* $maxdim / ($cpumax - $cpumin);# calculate the dimension of the bars
	}
	if ( $syst > $sysmax || $syst < $sysmin ) {                   # do the same for the system temp
	    print $remote "widget_set sensor alarm2 6 2 {ALARM!}\n";
	    $dim2 = 0;
	} else {
	    print $remote "widget_set sensor alarm2 6 2 {}\n";
	    $dim2 = ($syst - $sysmin )* $maxdim / ($sysmax - $sysmin);
	}
	print $remote "widget_set sensor bar1 6 1 $dim1\n";       # display the current bars
	print $remote "widget_set sensor bar2 6 2 $dim2\n";
	sleep 3;                                                 # wait some time
	chomp($rpm1 = getVal ( "$chip/$fan1sens" , 1 ));          # read the fan speeds
	chomp($rpm2 = getVal ( "$chip/$fan2sens" , 1 ));
	print $remote "widget_set fans rpm1 8 1 {$rpm1}\n";       # dispay the speeds
	print $remote "widget_set fans rpm2 8 2 {$rpm2}\n";
	sleep 3;                                                 # wait some time
    }
} else {  ## if the LCD has more than 2 lines

    # Set up some screen widgets
    print $remote "client_set name {Sensors}\n";                   # tell the server our name
    print $remote "screen_add sensor\n";                           # add a screen
    print $remote "widget_add sensor titel title\n";               # add a titel
    print $remote "widget_set sensor titel {$title}\n";            # and display it
    print $remote "widget_add sensor cpu string\n";                # add the cpu string
    print $remote "widget_add sensor ctemp string\n";              # add the string holding the cpu temp
    print $remote "widget_add sensor sys string\n";                # add the sys string
    print $remote "widget_add sensor stemp string\n";              # add the string holding the sys temp
    print $remote "widget_add sensor fan string\n";                # add the fan string
    print $remote "widget_add sensor rpm string\n";                # add the string holding the fan speeds
    print $remote "widget_add sensor alarm1 string\n";             # add the string indicating an alarm state
    print $remote "widget_add sensor alarm2 string\n";             # add the string indicating an alarm state
    print $remote "widget_add sensor bar1 hbar\n";                 # add the bar for the cpu temp
    print $remote "widget_add sensor bar2 hbar\n";                 # add the bar for the sys temp
    print $remote "widget_set sensor cpu 1 2 {CPU:}\n";            # display some things
    print $remote "widget_set sensor sys 1 3 {MB:}\n";
    print $remote "widget_set sensor fan 1 4 {Fan1,2:}\n";

    # do forever
    while(1) {


	chomp($cput = getVal ( "$chip/$cpusens" , 2 ));               # read all the value's
	chomp($syst = getVal ( "$chip/$syssens" , 2 ));
	chomp($rpm1 = getVal ( "$chip/$fan1sens" , 1 ));
	chomp($rpm2 = getVal ( "$chip/$fan2sens" , 1 ));
	print $remote "widget_set sensor ctemp $pos 2 {$cput}\n";     # display everything
	print $remote "widget_set sensor stemp $pos 3 {$syst}\n";
	print $remote "widget_set sensor rpm 10 4 {$rpm1 & $rpm2}\n";
	if ( $cput > $cpumax || $cput < $cpumin ) {                   # check if the temp is within range
	    print $remote "widget_set sensor alarm1 6 2 {ALARM!}\n";  # if not print ALARM
	    $dim1 = 0;                                                # set the bar's dimension to 0
	} else {
	    print $remote "widget_set sensor alarm1 6 2 {}\n";
	    $dim1 = ($cput - $cpumin )* $maxdim / ($cpumax - $cpumin);# calculate the dimension of the bars
	}
	if ( $syst > $sysmax || $syst < $sysmin ) {                   # do the same for the system temp
	    print $remote "widget_set sensor alarm2 6 3 {ALARM!}\n";
	    $dim2 = 0;
	} else {
	    print $remote "widget_set sensor alarm2 6 3 {}\n";
	    $dim2 = ($syst - $sysmin )* $maxdim / ($sysmax - $sysmin);
	}
	print $remote "widget_set sensor bar1 6 2 $dim1\n";           # display the current bars
	print $remote "widget_set sensor bar2 6 3 $dim2\n";
	sleep 3;                                                     # wait some time
    }
}

## help message
sub help {
    print <<EOM;

LCD-sensors $version
By Nick Van Helleputte

Displays data provided by lm-sensors on an LCD using LCDd provided by lcdproc.

Usage:      ./LCDsensors.pl [OPTIONS]

Options:    -h      Displays this message
            -v      Displays version

Important:  !! Be certain to edit the file and change the first variables 
            !! concerning LM-sensors to meet your specific system.

This script needs a working version of lm-sensors.
(see http://www2.lm-sensors.nu/~lm78/ for more details)

This script needs a working version of LCDd, the server daemon coming with the 
package lcdproc. (see http://lcdproc.omnipotent.net/ for more details)

This script is optimized for 16x2, 20x2, 20x4 displays. It will also output on
different sized displays but that won't look very nice. (A lot of waste).

Also check out https://nederwiet.wox.org/www/sensors-lcd/
A similar project where I found some inspiration.
EOM
exit 1;
} 

## subroutine to read a number out of a file
sub getVal {
    my ($filename, $index) = @_;      # first argument is where to read from, second is witch number to read
    
    open (FILE, $filename);           # open the file
    my $temp = <FILE>;                # store the contents
    close (FILE);
    
    my @veld = split (/ /, $temp);    # split up the contents
    return $veld[$index];             # return the wanted value
}

exit 1;  # normally, you will never come this far
```

Edit:
I have changed the script so that right correct sensor locations are used (I hope):
```
## variables regarding lm_sensors, update these conform to your system
my $chip='/sys';  # directory where lm_sensors writes its data
my $cpusens='/bus/pci/drivers/k8temp/0000:00:18.3/temp1_input';  # cpu sensor, in my case temp3
my $syssens='/devices/platform/it87.552/temp1_input';  # mobo sensor, in my case temp2
my $fan1sens='/devices/platform/it87.552/fan1_input';  # cpufan sensor
my $fan2sens='/devices/platform/it87.552/fan2_input';  # casefan sensor

## variables regarding LCDd, update if necessary, but normally these are correct
my $server='localhost';
my $port='13666';
```

Now the script works, but does not show any sensor data :(

---

### Post by sonicbuddha on 2009-04-07
A quick look at the script and the files its examining and it seems that, at least in previous versions of lm-sensors, the values for max, min, and actual temp as well as max, min, and actual fan speed were all kept in the same file.  Now these values are stored in separate files.  Not surprising there have been changes that break this since I believe this script as last updated 2002 (when /proc was the primary location for such info- my how time flies).  This is why you're getting empty temp values.  It won't take a Perl genius to fix it (which I'm not) but the script is surprisingly simple, just "read value and print it", and if I play with it, if only to get some experience writing lcdproc plugins, I'll post my results.  Or you can give it a go.

Example:
```

## determine minimum and maximum temperatures
$cpumax = getVal( "$chip/$cpusens" , 0 );
$cpumin = getVal( "$chip/$cpusens" , 1 );
```

And
```

chomp($cput = getVal ( "$chip/$cpusens" , 2 ));     # read the cpu temp
```


Hope that helps.

---

### Post by mrtomservo on 2009-04-11
Hi guys!  I was working on the very same thing, and if it weren't for Sonicbuddha I would have given up and moved on.  Playing around with the script, there seemed to be some syntax issues and obviously lmsensors uses different files for input/min/max.  It's working perfectly for me now.

Anyway, look for the "# EDITED" parts and you can see what I did.  Hope it works for everyone!

Here's my LCDsensors.pl:

```
#!/usr/bin/perl
########################################################################
## This is a perl script that outputs some data coming                ##
## from lm-sensors to an LCD.                                         ##
##                                                                    ##
## This script needs a working version of lm-sensors                  ##
## (see http://www2.lm-sensors.nu/~lm78/ for more details)            ##
## You need to change some variables below.                           ##
##                                                                    ##
## This script needs a working version of LCDd, the                   ##
## server daemon coming with the package lcdproc.                     ##
## (see http://lcdproc.omnipotent.net/ for more details)              ##
##                                                                    ##
## This script is optimized for 16x2, 20x2, 20x4 displays. It         ##
## will also output on different sized displays but that won't        ##
## look very nice. (A lot of waste). 40x2 or 40x4 are still           ##
## acceptable. If you have a different sized display, you should      ##
## change where the widgets are placed on the sreen.                  ##
## (http://lcdproc.omnipotent.net/netstuff.txt for more details)      ##
##                                                                    ##
## Also check out https://nederwiet.wox.org/www/sensors-lcd/          ##
## A similar project where I found some inspiration.                  ##
##                                                                    ##
## See the README for more details.                                   ##
##                                                                    ##
## The author:                                                        ## 
## Nick Van Helleputte, Belgium                                       ##
## May 2002                                                           ##
########################################################################

## --> CHANGE THESE VARIABLES !!!!!!
## variables regarding lm_sensors, update these conform to your system
my $chip='/sys/devices/platform/it87.2576';  # directory where lm_sensors writes its data
my $cpusens='temp3_input';  # EDITED, seperate files for sensors / cpu sensor, in my case temp3 
my $syssens='temp2_input';  # EDITED, seperate files for sensors / mobo sensor, in my case temp2
my $fan1sens='fan1_input';  # EDITED, seperate files for sensors / cpufan sensor
my $fan2sens='fan2_input';  # EDITED, seperate files for sensors / casefan sensor
my $cpumaxsens='temp3_max'; # EDITED, seperate files for sensors / new variable for cpumax
my $cpuminsens='temp3_min'; # EDITED, seperate files for sensors / new variable for cpumin
my $sysmaxsens='temp2_max'; # EDITED, seperate files for sensors / new variable for sysmax
my $sysminsens='temp2_min'; # EDITED, seperate files for sensors / new variable for sysmin

## variables regarding LCDd, update if necessary, but normally these are correct
my $server='localhost';
my $port='13666';

########################################################################
##                                                                    ##
## don't change the following unless you know what you're doing       ##
##                                                                    ##
########################################################################

## Check if the values above are correct
if (!-d "$chip") { 
    print "$chip not found! \n";
    print "Did you change the variables? Edit this file please.\n";
    exit 0;
}
if (!-e "$chip/$cpusens") {
    print "No cpu sensor found! \n";
    print "Did you change the variables? Edit this file please.\n";
    exit 0;
}

if (!-e "$chip/$syssens") {
    print "No system sensor found! \n";
    print "Did you change the variables? Edit this file please.\n";
    exit 0;
}

if (!-e "$chip/$fan1sens") {
    print "No cpufan sensor found! \n";
    print "Did you change the variables? Edit this file please.\n";
    exit 0;
}

if (!-e "$chip/$fan2sens") {
    print "No casefan sensor found! \n";
    print "Did you change the variables? Edit this file please.\n";
    exit 0;
}

## don't change these variables
my $cpumin;          # minimal cpu temperature as found in $cpusens
my $cpumax;          # maximal cpu temperature as found in $cpusens
my $sysmin;          # minimal system temperature as found in $syssens
my $sysmax;          # maximal system temperature as found in $syssens
my $cput;            # current cpu temperature
my $syst;            # current system temperature
my $rpm1;            # current speed of cpu fan
my $rpm2;            # current speed of casefan
my $dim1;            # dimension of cpubar
my $dim2;            # dimension of system bar
my $temp;            # temp variabele used for several purposes
my @veld;            # temp array
my $lcdwid;          # width of the lcd
my $lcdhgt;          # height of the lcd
my $title;           # title
my $pos;             # where the temps will be placed
my $maxdim;          # maximum allowable dimension of the bars
my $version='0.96';

use IO::Socket;
use Fcntl;
use Getopt::Std;
use strict;
use vars qw($opt_h $opt_v);


## evaluate the options
&getopts("hv")||die "ERROR: Illegal option. -h for help\n";
&help if ($opt_h);
if($opt_v) {
    print ("LCDsensors $version\n");
    exit 0;
}


## determine minimum and maximum temperatures
#$cpumax = getVal( "$chip/$cpusens" , 0 ); 
#$cpumin = getVal( "$chip/$cpusens" , 1 );
$cpumax = getVal( "$chip/$cpumaxsens" , 0 ); # EDITED, for newer multi file lmsensors, cpumaxsens
$cpumin = getVal( "$chip/$cpuminsens" , 1 ); # EDITED, for newer multi file lmsensors, cpuminsens


# do the same for the system temp
#$sysmax = getVal( "$chip/$syssens" , 0 );
#$sysmin = getVal( "$chip/$syssens" , 1 );
$sysmax = getVal( "$chip/$sysmaxsens" , 0 ); # EDITED, for newer multi file lmsensors, sysmaxsens
$sysmin = getVal( "$chip/$sysminsens" , 1 ); # EDITED, for newer multi file lmsensors, sysminsens

## create a titel
$_ = `hostname`;
#chomp($title = "LCDsensors running on $_");
chomp($title = "LCDsensors / $_"); # EDITED, just because I wanted to! :P


## Connect to the server
my $remote = IO::Socket::INET->new(
		Proto     => "tcp",
		PeerAddr  => $server,
		PeerPort  => $port,
	)
	|| die "Cannot connect to LCDproc at $server on port $port\n";

$remote->autoflush(1);       # Make sure our messages get there right away
sleep 1;	             # Give server plenty of time to notice us...
print $remote "hello\n";     # tell the server we're here
$temp = <$remote>;           # read the server's answer
@veld = split(/ /,$temp);    # split up the contents
$lcdwid=$veld[7];            # read the lcd's dimensions
$lcdhgt=$veld[9];

# Turn off blocking mode...
fcntl($remote, F_SETFL, O_NONBLOCK);

## define where the widgets will be placed
$pos = $lcdwid - 2;              # temps will be placed next to right edge
$maxdim = 5 * ( $lcdwid - 8 );   # max ($lcdwid - 8) characters for the bars

## do folowing if an LCD with 2 lines is attached
if ($lcdhgt eq '2' ) {

    # Set up some screen widgets
    print $remote "client_set name {Sensors}\n";                   # tell the server our name
    print $remote "screen_add sensor\n";                           # add a sensor screen
    print $remote "widget_add sensor cpu string\n";                # add the cpu string
    print $remote "widget_add sensor ctemp string\n";              # add the string holding the cpu temp
    print $remote "widget_add sensor sys string\n";                # add the sys string
    print $remote "widget_add sensor stemp string\n";              # add the string holding the sys temp
    print $remote "widget_add sensor alarm1 string\n";             # add the string indicating an alarm state
    print $remote "widget_add sensor alarm2 string\n";             # add the string indicating an alarm state
    print $remote "widget_add sensor bar1 hbar\n";                 # add the bar for the cpu temp
    print $remote "widget_add sensor bar2 hbar\n";                 # add the bar for the sys temp
    print $remote "widget_set sensor cpu 1 1 {CPU:}\n";            # put 'CPU:' on the screen
    print $remote "widget_set sensor sys 1 2 {MB:}\n";             # put 'MB:' on the screen

    print $remote "screen_add fans\n";                             # add a fan screen
    print $remote "widget_add fans fan1 string\n";                 # add the fan1 string
    print $remote "widget_add fans rpm1 string\n";                 # add the string holding the fan1 speed
    print $remote "widget_add fans fan2 string\n";                 # add the fan2 string
    print $remote "widget_add fans rpm2 string\n";                 # add the string holding the fan2 speed
    print $remote "widget_set fans fan1 1 1 {Fan1:       rpm}\n";  # put some things on the screen
    print $remote "widget_set fans fan2 1 2 {Fan2:       rpm}\n";

    # do forever
    while(1) {

	chomp($cput = getVal ( "$chip/$cpusens" ));                   # EDITED, read the cpu temp properly
	chomp($syst = getVal ( "$chip/$syssens" ));                   # EDITED, read the system temp properly
#	chomp($cput = getVal ( "$chip/$cpusens" , 2 ));               # read the cpu temp
#	chomp($syst = getVal ( "$chip/$syssens" , 2 ));               # read the system temp
	print $remote "widget_set sensor ctemp $pos 1 {$cput}\n";     # display the current temperatures
	print $remote "widget_set sensor stemp $pos 2 {$syst}\n";
	if ( $cput > $cpumax || $cput < $cpumin ) {                   # check if the temp is within range
	    print $remote "widget_set sensor alarm1 6 1 {ALARM!}\n";  # if not print ALARM
	    $dim1 = 0;                                                # set the bar's dimension to 0
	} else {
	    print $remote "widget_set sensor alarm1 6 1 {}\n";        # clear the ALARM
	    $dim1 = ($cput - $cpumin )* $maxdim / ($cpumax - $cpumin);# calculate the dimension of the bars
	}
	if ( $syst > $sysmax || $syst < $sysmin ) {                   # do the same for the system temp
	    print $remote "widget_set sensor alarm2 6 2 {ALARM!}\n";
	    $dim2 = 0;
	} else {
	    print $remote "widget_set sensor alarm2 6 2 {}\n";
	    $dim2 = ($syst - $sysmin )* $maxdim / ($sysmax - $sysmin);
	}
	print $remote "widget_set sensor bar1 6 1 $dim1\n";       # display the current bars
	print $remote "widget_set sensor bar2 6 2 $dim2\n";
	sleep 3;                                                 # wait some time
	chomp($rpm1 = getVal ( "$chip/$fan1sens" ));          # EDITED, read the fan speeds properly
	chomp($rpm2 = getVal ( "$chip/$fan2sens" ));
#	chomp($rpm1 = getVal ( "$chip/$fan1sens" , 1 ));          # read the fan speeds
#	chomp($rpm2 = getVal ( "$chip/$fan2sens" , 1 ));
	print $remote "widget_set fans rpm1 8 1 {$rpm1}\n";       # dispay the speeds
	print $remote "widget_set fans rpm2 8 2 {$rpm2}\n";
	sleep 3;                                                 # wait some time
    }
} else {  ## if the LCD has more than 2 lines

    # Set up some screen widgets
    print $remote "client_set name {Sensors}\n";                   # tell the server our name
    print $remote "screen_add sensor\n";                           # add a screen
    print $remote "widget_add sensor titel title\n";               # add a titel
    print $remote "widget_set sensor titel {$title}\n";            # and display it
    print $remote "widget_add sensor cpu string\n";                # add the cpu string
    print $remote "widget_add sensor ctemp string\n";              # add the string holding the cpu temp
    print $remote "widget_add sensor sys string\n";                # add the sys string
    print $remote "widget_add sensor stemp string\n";              # add the string holding the sys temp
    print $remote "widget_add sensor fan string\n";                # add the fan string
    print $remote "widget_add sensor rpm string\n";                # add the string holding the fan speeds
    print $remote "widget_add sensor alarm1 string\n";             # add the string indicating an alarm state
    print $remote "widget_add sensor alarm2 string\n";             # add the string indicating an alarm state
    print $remote "widget_add sensor bar1 hbar\n";                 # add the bar for the cpu temp
    print $remote "widget_add sensor bar2 hbar\n";                 # add the bar for the sys temp
    print $remote "widget_set sensor cpu 1 2 {CPU:}\n";            # display some things
    print $remote "widget_set sensor sys 1 3 {MB:}\n";
    print $remote "widget_set sensor fan 1 4 {Fan1,2:}\n";

    # do forever
    while(1) {


	chomp($cput = getVal ( "$chip/$cpusens" , 2 ));               # read all the value's
	chomp($syst = getVal ( "$chip/$syssens" , 2 ));
	chomp($rpm1 = getVal ( "$chip/$fan1sens" , 1 ));
	chomp($rpm2 = getVal ( "$chip/$fan2sens" , 1 ));
	print $remote "widget_set sensor ctemp $pos 2 {$cput}\n";     # display everything
	print $remote "widget_set sensor stemp $pos 3 {$syst}\n";
	print $remote "widget_set sensor rpm 10 4 {$rpm1 & $rpm2}\n";
	if ( $cput > $cpumax || $cput < $cpumin ) {                   # check if the temp is within range
	    print $remote "widget_set sensor alarm1 6 2 {ALARM!}\n";  # if not print ALARM
	    $dim1 = 0;                                                # set the bar's dimension to 0
	} else {
	    print $remote "widget_set sensor alarm1 6 2 {}\n";
	    $dim1 = ($cput - $cpumin )* $maxdim / ($cpumax - $cpumin);# calculate the dimension of the bars
	}
	if ( $syst > $sysmax || $syst < $sysmin ) {                   # do the same for the system temp
	    print $remote "widget_set sensor alarm2 6 3 {ALARM!}\n";
	    $dim2 = 0;
	} else {
	    print $remote "widget_set sensor alarm2 6 3 {}\n";
	    $dim2 = ($syst - $sysmin )* $maxdim / ($sysmax - $sysmin);
	}
	print $remote "widget_set sensor bar1 6 2 $dim1\n";           # display the current bars
	print $remote "widget_set sensor bar2 6 3 $dim2\n";
	sleep 3;                                                     # wait some time
    }
}

## help message
sub help {
    print <<EOM;

LCD-sensors $version
By Nick Van Helleputte

Displays data provided by lm-sensors on an LCD using LCDd provided by lcdproc.

Usage:      ./LCDsensors.pl [OPTIONS]

Options:    -h      Displays this message
            -v      Displays version

Important:  !! Be certain to edit the file and change the first variables 
            !! concerning LM-sensors to meet your specific system.

This script needs a working version of lm-sensors.
(see http://www2.lm-sensors.nu/~lm78/ for more details)

This script needs a working version of LCDd, the server daemon coming with the 
package lcdproc. (see http://lcdproc.omnipotent.net/ for more details)

This script is optimized for 16x2, 20x2, 20x4 displays. It will also output on
different sized displays but that won't look very nice. (A lot of waste).

Also check out https://nederwiet.wox.org/www/sensors-lcd/
A similar project where I found some inspiration.
EOM
exit 1;
} 

## subroutine to read a number out of a file
sub getVal {
    my ($filename, $index) = @_;      # first argument is where to read from, second is witch number to read
    
    open (FILE, $filename);           # open the file
    my $temp = <FILE>;                # store the contents
    close (FILE);
    
    my @veld = split (/ /, $temp);    # split up the contents
    return $veld[$index];             # return the wanted value
}

exit 1;  # normally, you will never come this far
```

---

