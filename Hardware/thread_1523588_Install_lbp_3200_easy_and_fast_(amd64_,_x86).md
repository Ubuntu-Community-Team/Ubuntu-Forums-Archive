---
title: "Install lbp 3200 easy and fast (amd64 , x86)"
date: 2010-07-03
forum: Hardware
---

### Post by Fitmoos on 2010-07-03
Esta es una guia chilena para la LBP 3200.
Sirve para amd64 y x86, en ubuntu 10.04 (no se si para debian)

Install this: 
sudo apt-get install build-essential libstdc++6-4.4-dev debhelper autoconf libglib2.0-dev libgtk2.0-dev libltdl-dev libgpg-error-dev libcups2-dev libxml2-dev libcupsys2

Donwload this
[http://support-sg.canon-asia.com/contents/SG/EN/0900772407.html](http://support-sg.canon-asia.com/contents/SG/EN/0900772407.html)

Unpackage with your's zipper
and open the directory

cd .../CAPT_Printer_Driver_for_Linux_V200_uk_EN/Driver/Debian

and install

sudo dpkg -i --force-architecture cndrvcups-common_2.00-2_i386.deb
sudo dpkg -i --force-architecture cndrvcups-capt_2.00-2_i386.deb


continue in the six (6) step here :

[http://ubuntu-utah.ubuntuforums.org/showthread.php?p=8595445](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=8595445)

> **rajamohan said:**
> 
Step6 &#8211; Editing the startup script for starting CAPT daemon

I had modified the ccpd startup script to make it little polished

```

#!/bin/sh
# startup script for Canon Printer Daemon for CUPS (ccpd)
# Modified for Debian GNU/Linux


DAEMON=/usr/sbin/ccpd
LOCKFILE=/var/lock/subsys/ccpd
NAME=ccpd
DESC="Canon Printer Daemon for CUPS"

test -f $DAEMON || exit 0

. /lib/lsb/init-functions

export PATH=$PATH:/usr/local/sbin:/usr/local/bin

ccpd_start ()
{
    log_begin_msg "Starting $DESC: $NAME"
        start-stop-daemon --start --quiet --oknodo --exec ${DAEMON}
        log_end_msg $?
}

ccpd_stop ()
{
        log_begin_msg "Stopping $DESC: $NAME"
    start-stop-daemon --stop --quiet --oknodo --signal 15 --exec ${DAEMON}
        log_end_msg $?
}


case $1 in

    start)
        ccpd_start
        ;;
        
    stop)
        ccpd_stop
        ;;
    
    status)
            echo "$DESC: $NAME:" `pidof $NAME`
        ;;
    
    restart)
            log_begin_msg "Restarting $DESC: $NAME"
        ccpd_stop
            sleep 2
        ccpd_start
            log_end_msg $?
        ;;
    
    *)
            echo "Usage: ccpd {start|stop|restart|status}"
        exit 1
        ;;
esac
exit 0

```Lets us start editing the script

delete all existing content and replace with the above script, save and close the editor

cd /etc/init.d 
sudo cp ccpd ccpd-old 
sudo gedit ccpd

Step7 &#8211; Setting the printer for CUPS

sudo /etc/init.d/cups restart 
sudo /usr/sbin/lpadmin -p LBP3200 -P /usr/share/cups/model/CNCUPSLBP3200CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E

This will add printer LBP3200

Step8 &#8211; Setting the printer for CAPT

sudo /usr/sbin/ccpdadmin -p LBP3200 -o /dev/usb/lp0

This will add printer LBP3200 to the CAPT monitor (daemon)

Step9 &#8211; Automating CAPT while booting the system

sudo update-rc.d ccpd defaults 50

Edit*
We are using 50 which means the ccpd is one the the last daemons to start This point is noted by _TommyBoy_

Step10 &#8211; Finalisation
reset




The lbp 3200 is very  slow in linux. The heavy document prints in windows.

No hablo ingles. =D

---

