---
title: "Canon printers insufficient supported - LBP2900B"
date: 2009-06-06
forum: Hardware
---

### Post by bluelightav on 2009-06-06
Dear community,

This is a sad story about a printer who wanted to work under Ubuntu and is still facing problems. Not that it isn't a good printer- no!

The black and white laser printer Canon LBP2900B is a economical printing solution for home and small offices. It comes with a driver supplied by Canon and so we thought that will be a piece of cake....
It turned into a story which we want to tell here.
We downloaded and installed the driver according to Canon's instructions.
After connecting the printer it prints fine until somehow the USB connection gets lost. After that the printer is not responsive.
Turning the printing off and on doesn't fix the problem. If you don't want to reboot the computer to get a functional printer again a manual restart of cups and  ccpd (Canon printer daemon) and the status monitor will fix it - but...

Our conclusion for now:
Auroville is an NGO with approximately 1200 people working in various departments. We have around 200 office spaces and it was decide to move as much as possible to open source software in the coming years. So far the hardware purchased for this project is of a mixed character in regards to the printers and scanners. 
Migrating our offices to Linux we definitely experience restrictions in terms of hardware choice but found that HP printer in general are better supported than others. However, we are very interested in Canon products as long we get the support needed to run them under Linux (Ubuntu). 
Unfortunately the migration of 6 offices are pending for the moment because of problems with the Canon drivers and we are not purchasing new Canon hardware since about one month for the same reason. We are not in the position to pause the hardware purchase any longer as some printers have to be replaced and given the present situation we have to fall back to HP products for the time being. 
We would be delighted to get a more energetic and focused support from Canon to be able to consider the use of Canon products in the future. 
Given the general movement worldwide of developing countries to move to properly licensed open source software it would be a great opportunity for Canon in India to support this movement with well supported hardware.

So we contacted Canon to get their support. After 2 months of emailing the only solution offered by Canon so far is to manually restart all the daemons. We explained this to our recently migrated grand mother but she found it too complicated as she is not yet familiar with the shell. The proposed solution from Canon is not suitable for end users on Ubuntu.

We looked into the issue ourselves and came up with the following solution:

After the initial printer driver installation under Hardy Heron:

[http://software.canon-europe.com/software/0031118.asp](http://software.canon-europe.com/software/0031118.asp)
```

cd ~/Desktop/CANON_UK/Driver/Debian/ 
sudo su
dpkg -i cndrvcups-common_1.80-1_i386.deb 
aptitude install libstdc++5 
dpkg -i cndrvcups-capt_1.80-1_i386.deb 
/etc/init.d/cupsys restart 
/usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E 
/usr/sbin/ccpdadmin -p LBP2900 -o /dev/usblp0 
/etc/init.d/ccpd start

```

The solution from Canon to simply restart the ccpd sometimes leaves the status monitor at a stage that it cannot reconnect to cups as a socket is still in use. The Status Monitor requires a user input in form of a click on the OK button to proceed with the printing. But the user can only see this if the Status Monitor is running. Therefore cups also has to be restarted to get the full functionality again.

The actual problem is the way Canon programmed their driver. The ccpd  crashes when it cannot see the printer or when cups is not running.

We wanted to come up with a more automated solution than posted here: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)

We based the restart on the error messages in dmesg. Please feel free to improve the script or/and give feedback.

Safe the following bash script as /etc/init.d/ccpd-fixd and chmod 755 /etc/init.d/ccpd-fixd

```

#!/bin/bash

## /etc/init.d/ccpd-fix : starts/stops/restarts the Canon CCPD-Fix Script

## Variable Definitions
# Path to binaries
PATH=/bin:/usr/bin:/sbin:/usr/sbin
# Path to the CCPD-Fix Script
DAEMON=/usr/sbin/ccpd-fix
# Optional : defines name and description of the deamon we are controling
NAME="ccpd-fixd"
DESC="Fix for CCPD"

## Beginning of the script
# Making sure the daemon is executable.
test -x $DAEMON || exit 0

# Action Control
case "$1" in
    start)
        echo "Starting $DESC: $NAME."
        $DAEMON & >& /dev/null
        echo ". Done."
        ;;
    stop)
        echo "Stopping $DESC: $NAME"
        killall -9 $DAEMON >& /dev/null
        #pkill $DAEMON >& /dev/null
        echo ". Stopped."
        ;;
    restart)
        echo "Restarting $DESC: $NAME"
        if [ -z "$(ps ax | egrep ccpd-fix )" ]; then
             echo "ccpd-fix is not running, I couldn't kill it."
        else
         killall -9 $DAEMON >& /dev/null
         #pkill $DAEMON >& /dev/null
        fi
        sleep 1
        $DAEMON & >& /dev/null
        echo ". Done"
        ;;
    *)
        echo "Usage: /etc/init.d/$NAME start|stop|restart" >&2
        exit 0
        ;;
esac
exit 0 

```



This perl script should be safed as /usr/sbin/ccpd-fix and then run 
chmod 755 /usr/sbin/ccpd-fix
```

#!/usr/bin/perl -w
use strict;

`logger **** CCPD Fix Started`;
sub get_last_segfault {
    my $timestamp = 0;
    my $line = `dmesg | grep ccpd | grep segfault| tail -1`;
    if ($line =~ m/(\d+\.\d+).*/){
$timestamp = $1;
    }
    return $timestamp;
}

sub printer_present {
    my $value = `lsusb | grep 04a9:2676 | wc -l`;
    `echo -n "CCPD Fix : Canon Printer Present: $value" | logger`;
    return $value;

}

my $last_segfault = 0;
my $treated_segfault = 0;

while (1) {
    if (printer_present() != 0) {
$last_segfault = get_last_segfault();
if ($last_segfault ne $treated_segfault) {
`echo -n "CCPD Fix : New segfault happend: $last_segfault but we last treated $treated_segfault" | logger`;
kill_and_restart();
$treated_segfault = $last_segfault;
}
    }
    `sleep 10`;
}

sub kill_and_restart {
# kill all running ccpdaemons
    while (my @pid_ccpd = split(' ' , `pidof ccpd`)) {
foreach (@pid_ccpd) {
`echo -n "CCPD Fix : killing ccpd process id $_ \n" | logger`;
`kill -9 $_`;
}
    }

# shutdown cups
    `/etc/init.d/cupsys stop`;

# kill all running captstatusui
    while (my @pid_captstatusui = split(' ' , `pidof captstatusui`)) {
foreach my $pid (@pid_captstatusui) {
`echo -n "CCPD Fix : killing ui process id $pid \n" | logger`;
`kill -9 $pid`;
}
    }

#my $username= `who | grep tty | cut -d' ' -f1`;


    `sleep 3`;
    `/etc/init.d/cupsys start`;
    `sleep 1`;
    `/etc/init.d/ccpd start`;
    `sleep 1`;

#`su $username -c "captstatusui -P LBP2900 &"`;
    `logger *** CCPD Fix : Job's Done`; 

```

If this works for you and you want to make it more permanent then add scripts in init.d to the required runlevels
```

update-rc.d ccpd-fix defaults 30
update-rc.d ccpd default 21

```

---

### Post by bluelightav on 2009-09-14
Hey, there is good news! Finally Canon looked into this issue and came out with a new driver. We tested it and it works. This printer is supported.
Follow this link to download the driver;

[http://support-in.canon-asia.com/contents/IN/EN/0900772410.html](http://support-in.canon-asia.com/contents/IN/EN/0900772410.html)

Thank you Canon for your effort and time!

The Blue Light team.

---

### Post by imcool on 2010-02-08
> **bluelightav said:**
> Hey, there is good news! Finally Canon looked into this issue and came out with a new driver. We tested it and it works. This printer is supported.
Follow this link to download the driver;

[http://support-in.canon-asia.com/contents/IN/EN/0900772410.html](http://support-in.canon-asia.com/contents/IN/EN/0900772410.html)

Thank you Canon for your effort and time!

The Blue Light team.

better have a look again its the solution for 2900 not 2900B .

---

### Post by bluelightav on 2010-02-08
> **imcool said:**
> better have a look again its the solution for 2900 not 2900B .
They have only one solution for all  printers and their driver doesn't work.

We are having problems with this printer. At the moment we can't recommend it.

---

### Post by smydtt on 2010-04-22
Please try the following link. It is meant for LBP 2900 but works for my LBP 2900B.
[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

---

### Post by manpreetsv on 2010-07-18
Hi, 

 Canon 2900B printer driver correct link is :-
[http://support-in.canon-asia.com/contents/IN/EN/0900772407.html](http://support-in.canon-asia.com/contents/IN/EN/0900772407.html)

Download and follow the instructions . 

I've got my printer running with Ubuntu 10.04

Regards

---

