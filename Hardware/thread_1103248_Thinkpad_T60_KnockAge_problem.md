---
title: "Thinkpad T60 KnockAge problem"
date: 2009-03-22
forum: Hardware
---

### Post by Xcorp on 2009-03-22
I've followed this guide page [http://www.ibm.com/developerworks/linux/library/l-knockage.html](http://www.ibm.com/developerworks/linux/library/l-knockage.html) to setup knockAge on my T60 but I have some problems. The first one is when I record knocks

```
xcorp@Haxxor:~/src$ ./knockAge-0.1.pl -c
Prototype mismatch: sub main::__LONG_MAX__ () vs none at /usr/lib/perl/5.10/_h2ph_pre.ph line 291.
Constant subroutine __LONG_MAX__ redefined at /usr/lib/perl/5.10/_h2ph_pre.ph line 291.
enter a knock sequence:
Knock: 0 ## last: [8567639621] curr: [0] difference is: 0
Knock: 1 ## last: [8568167681] curr: [8567794586] difference is: 373095
Knock: 2 ## last: [8568510615] curr: [8568203679] difference is: 306936
Knock: 3 ## last: [8570956790] curr: [8568670578] difference is: 2286212
Knock: 4 ## last: [8570106637] curr: [8570956790] difference is: 850153
Knock: 5 ## last: [8570239619] curr: [8570106637] difference is: 132982
place the following line in /home/xcorp/.knockFile

0 373095 306936 2286212 850153 132982 _#_ (command here) _#_ <comments here>

xcorp@Haxxor:~/src$
```
It looks like it's succesfull, but does the errors matter?

The second one:
```
xcorp@Haxxor:~/src$ ./knockAge-0.1.pl
Prototype mismatch: sub main::__LONG_MAX__ () vs none at /usr/lib/perl/5.10/_h2ph_pre.ph line 291.
Constant subroutine __LONG_MAX__ redefined at /usr/lib/perl/5.10/_h2ph_pre.ph line 291.
Use of uninitialized value in system at ./knockAge-0.1.pl line 236.
Use of uninitialized value in system at ./knockAge-0.1.pl line 236.
Use of uninitialized value in system at ./knockAge-0.1.pl line 236.
Use of uninitialized value in system at ./knockAge-0.1.pl line 236.
Use of uninitialized value in system at ./knockAge-0.1.pl line 236.
Use of uninitialized value in system at ./knockAge-0.1.pl line 236.
Use of uninitialized value in system at ./knockAge-0.1.pl line 236.
Use of uninitialized value in system at ./knockAge-0.1.pl line 236.
Use of uninitialized value in system at ./knockAge-0.1.pl line 236.
^C
xcorp@Haxxor:~/src$

```
This is the response when I try to run the program, if I don't CTRL+C it just keeps spamming the error. I've tried to knock but the command i've told to be executed never runs.
Has anyone got this to work?

---

### Post by Xcorp on 2009-04-02
Bump?

---

### Post by Deichscheich on 2010-10-22
Yeah, same here... I have no idea about perl, so ... no idea!

Linux Mint 10 RC (Ubuntu 10.10)
ThinkPad X60

The Problem is supposed to be in the highlighted line 236

```
#!/usr/bin/perl -w  # readKnocks.pl 
# heavily influenced by hdaps-gl.c from Jeff Molofee

use strict;
require 'sys/syscall.ph';  # for subsecond timing

my $option = $ARGV[0] || ""; # simple option handling

# filename for hdaps sensor reads
my $hdapsFN = "/sys/devices/platform/hdaps/position";


my $UPDATE_THRESHOLD =   4;      # threshold of force that indicates a knock
my $INTERVAL_THRESHOLD = 100000; # microseconds of time required between knock
                                 # events
my $SLEEP_INTERVAL =     0.01;   # time to pause between hdaps reads
 
my $MAX_TIMEOUT_LENGTH = 4;      # maximum length in seconds of knock pattern
                                 # length
my $MAX_KNOCK_DEV =      100000; # maximum acceptable deviation between recorded
                                 # pattern values and knocking values

my $LISTEN_TIMEOUT =     2;      # timeout value in seconds between knock 
                                 # events when in listening mode



my @baseKnocks = ();             # contains knock intervals currently entered
my %knockHash = ();              # contains knock patterns, associated commands

my $prevInterval =       0;      # previous interval of time
my $knockCount =         0;      # current number of knocks detected

my $restX = 0; # `resting' positiong of X axis accelerometer
my $restY = 0; # `resting' positiong of Y axis accelerometer
my $currX = 0; # current position of X axis accelerometer
my $currY = 0; # current position of Y axis accelerometer
my $lastX = 0; # most recent position of X axis accelerometer
my $lastY = 0; # most recent position of Y axis accelerometer


my $startTime = 0;  # to manage timeout intervals
my $currTime  = 0;  # to manage timeout intervals
my $timeOut   = 0;  # perpetual loop variable
my $knockAge  = 0;  # count of knocks to cycle time interval

# checkAccelerometer ensures accelerometer availability
sub checkAccelerometer() {

  my $ret;
  $ret = readPosition ();
  if( $ret ){
    print "no accelerometer data available - tis bork ed\n";
    exit(1);
  }
    
}#checkAccelerometer

sub getEpochMicroSeconds {

  my $TIMEVAL_T = "LL";      # LL for microseconds
  my $timeVal = pack($TIMEVAL_T, ());

  syscall(&SYS_gettimeofday, $timeVal, 0) != -1 or die "micore seconds: $!";
  my @vals =  unpack( $TIMEVAL_T, $timeVal );
  $timeVal = $vals[0] . $vals[1];
  $timeVal = substr( $timeVal, 6);

  my $padLen =  10 - length($timeVal);
  $timeVal = $timeVal . "0" x $padLen;

  return($timeVal);
}#getEpochMicroSeconds


sub getEpochSeconds {
  my $TIMEVAL_T = "LL";      # LL for microseconds
  my $start = pack($TIMEVAL_T, ());
  syscall(&SYS_gettimeofday, $start, 0) != -1 or die "seconds: $!";
  return( (unpack($TIMEVAL_T, $start))[0] );
}#getEpochSeconds

## comments from Jeff Molofee in hdaps-gl.c
#* read_position - read the (x,y) position pair from hdaps.
#*
#* We open and close the file on every invocation, which is lame but due to
#* several features of sysfs files:
#*
#*	(a) Sysfs files are seekable.
#*	(b) Seeking to zero and then rereading does not seem to work.
##
sub readPosition() {

  my ($posX, $posY) = "";
  my $fd = open(FH," $hdapsFN");

    while( <FH> ){
      s/\(//g;
      s/\)//g;
      ($posX, $posY) = split ",";
      
    }# while read

  close(FH);

  return( $posX, $posY );

}#readPosition


# knockListen processes the accelerometer data and records knock events.
sub knockListen() {

  my $checkKnock = 0;
  ($currX, $currY) = readPosition();
  
  $currX -= $restX;  # adjust for rest data state
  $currY -= $restY;  # adjust for rest data state


  # require a high threshold of acceleration to ignore non-events like
  # bashing the enter key or hitting the side with the mouse... this would
  # be a good place to enter specific code for what to do when you can't 
  # take it anymore and put your boot through the LCD
  if( abs ($currX) > $UPDATE_THRESHOLD) {
    $checkKnock = 1;
  }

  if( abs ($currY) > $UPDATE_THRESHOLD) {
    $checkKnock = 1;
  }

  
  if( $checkKnock == 1 ){

    my $currVal = getEpochMicroSeconds();
    my $diffInterval = abs($prevInterval - $currVal);

    # hard knock events can create continuous acceleration across a large time
    # threshold.  requiring an elapsed time between knock events effectively 
    # reduces what appear as multiple events according to sleep_interval and
    # update_threshold into a singular event.
    if(  $diffInterval > $INTERVAL_THRESHOLD ){

      if( $knockCount == 0 ){ $diffInterval = 0 }

      if( $option ){
        print "Knock: $knockCount ## last: [$currVal] curr: [$prevInterval] ";
        print "difference is: $diffInterval\n";
      }

      push @baseKnocks, $diffInterval;
      $knockCount++;

    }# if the difference interval is greater than the threshold
  
    $prevInterval = $currVal;
 
  }#if checkknock passed

}#knockListen





# readKnockFile reads knock sequences and commands from ~/.knockfile
# format is:  knock sequence _#_ command _#_ comments
sub readKnockFile {

  open(KNCKFILE,"$ENV{HOME}/.knockFile") or die "no knock file: $!";

    while(<KNCKFILE>){

      if( !/^#/ ){

        my @arrLine = split "_#_";
        $knockHash{ $arrLine[0] }{ cmd }     = $arrLine[1];
        $knockHash{ $arrLine[0] }{ comment } = $arrLine[2];
      
      }#if not a comment line

    }#for each line in file

  close(KNCKFILE);

}#readKnockFile




# compareKnockSequences checks the currently entered knock with all knock
# sequences read from ~/.knockFile
sub compareKnockSequences {

  my $countMatch = 0;  # record how many knocks matched

  # for each knock sequence in the config file 
  for( keys %knockHash ){
   
    # get the timings between knocks 
    my @confKnocks = split;

    # if the count of knocks match
    if( $knockCount eq @confKnocks ){

      my $knockDiff = 0;
      my $counter = 0;

      for( $counter=0; $counter<$knockCount; $counter++ ){
        
        $knockDiff = abs($confKnocks[$counter] - $baseKnocks[$counter]);
        my $knkStr = "k $counter b $baseKnocks[$counter] ".
                     "c $confKnocks[$counter] d $knockDiff\n"; 

        # if it's an exact match, increment the matching counter
        if( $knockDiff < $MAX_KNOCK_DEV ){
          
          if( $option ){ print "MATCH $knkStr" }
          $countMatch++;
        
        # if the knocks don't match, move on to the next pattern in the list
        }else{

          if( $option ){ print "DISSONANCE $knkStr" }
          last;

        }# deviation check

      }#for each knock

    }#if number of knocks matches

    # if the count of knocks is an exact match, run the command
    if( $countMatch eq @confKnocks ){  
**      my $cmd = system( $knockHash{"@confKnocks "}{ cmd } );**
      if( $option ){ print "$cmd\n" }
      last;

    # otherwise, make the count of matches zero, in order to not reset
    }else{
      $countMatch = 0;
    }
    
  }#for keys


  # if the match count is zero, exit and don't reset variables so a longer 
  # knock sequence can be entered and checked
  if( $countMatch == 0 ){ return() }

  # if a match occured, reset the variables so it won't match another pattern
  $knockCount = 0;
  @baseKnocks = ();

}#compareKnockSequences


# begin main program logic

# setup the default position of the hdaps sensor values
($restX, $restY ) = readPosition();

# if -c specified on command line, run the create pattern code
# tap in your knock, and when the timeout has expired since the last
# knock, print out the knock and exit the program
if( $option eq "-c" ){

  print "enter a knock sequence:\n";

  $startTime = getEpochSeconds();  # reset time out start

  while( $timeOut == 0 ){

    $currTime = getEpochSeconds(); 
 
    # check if there has not been a knock in a while 
    if( $currTime - $startTime > $MAX_TIMEOUT_LENGTH ){
  
      $timeOut = 1;  # exit the loop
  
    }else{
 
      # if a knock has been entered before timeout, reset timers so
      # more knocks can be entered
 
      if( $knockCount != $knockAge ){
        $startTime = $currTime;   # reset timer for longer delay
        $knockAge = $knockCount;  # synchronize knock counts
      }# if a new knock came in
  
    }# if timer not reached
  
    knockListen();
    select(undef, undef, undef, $SLEEP_INTERVAL);           
  
  }#timeOut =0

  if( @baseKnocks ){
    print "place the following line in $ENV{HOME}/.knockFile\n\n";
    for( @baseKnocks ){ print "$_ " }
    print "_#_ (command here) _#_ <comments here>\n\n";
  }#if knocks entered


# if -c is not specified, run the code to detect knocks
# read the ~/.knockFile configuration file, then compare any knock sequence
# of knock events that come in
}else{

  # main code loop to listen for knocking and run commands
  readKnockFile();

  $startTime = getEpochSeconds();

  while( $timeOut == 0 ){

    $currTime = getEpochSeconds();

    if( $currTime - $startTime > $LISTEN_TIMEOUT ){

      $knockCount = 0;
      @baseKnocks = ();
      $startTime = $currTime;
      if( $option ){ print "listen timeout - resetting knocks \n" }
 
    }else{

      if( $knockCount != $knockAge ){
        $startTime = $currTime;   # reset timer for longer delay
        $knockAge = $knockCount;  # synchronize knock counts
      }# if a new knock came in

      compareKnockSequences();

    }#if not reset timeout 

    knockListen();

    select(undef, undef, undef, $SLEEP_INTERVAL);           

  }#main knock listen loop

}# if create or listen for knocks

# EOF
```

---

