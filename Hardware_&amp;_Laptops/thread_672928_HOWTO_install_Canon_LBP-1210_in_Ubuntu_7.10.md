---
title: "HOWTO: install Canon LBP-1210 in Ubuntu 7.10"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by notepad on 2008-01-20
How to install the Canon LBP-1210 printer on Ubuntu 7.10!

This howto was based entirely on the howto at 
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)
all credit to the author.

I have adapted those instructions to make it easier for people with the
LBP-1210 printer to follow without having to try to figure out what arguments
to substitute in certain places and to caution people away from worrying about
things that might lead them astray.

note that this howto is specifically written for the LBP-1210 printer on Ubuntu 7.10.



step 1:

go to [http://software.canon-europe.com/products/0000525.asp](http://software.canon-europe.com/products/0000525.asp) and download
the Canon CAPT Printer Driver for Linux (1.30)

the filename is Driver.tar.gz

please note that the canon website mentions that you must install ghostscript
for the driver to work. ignore this. you do not need to install ghostscript.


step 2:

double click on the driver file you just downloaded. it is a tarred gunzip archive
which will automatically open with file roller when you double click on it.

hit the extract button to extract the contents of the archive to your desktop.


step 3:

we will use a program called alien to convert the extracted files into debian
packages. we first need to install alien since it doesnt come with ubuntu.

run a terminal by going to Applications > Accessories > Terminal

type the following command;

sudo aptitude install alien

follow the prompts in the terminal to proceed with the installation. note that i needed
to insert my ubuntu 7.10 cd to complete the installation so have yours ready.


step 4:

we can now use alien to convert the *rpm files to the *.deb files that we need.

note that the following commands depend on you having extracted the contents of
the driver archive to your desktop.

issue the following commands in the terminal once the installation of alien is complete;

cd Desktop/Driver
sudo alien -c cndrvcups*
sudo dpkg -i *.deb


step 5:

stop cupsys with the following command in your terminal;

sudo /etc/init.d/cupsys stop


step 6:

we need to change some permissions with the following commands in your terminal;

sudo chmod 777 /var/ccpd/fifo0
sudo chmod -R a+rX /usr/share/cups/model


step 7:

we can restart cupsys with the following command in your terminal;

sudo /etc/init.d/cupsys start


step 8:

now we are into the good stuff where we register the printer driver. issue the following
commands in your terminal;

sudo /usr/sbin/lpadmin -p LBP1210 -m CNCUPSLBP1210CAPTJ.ppd -v ccp:/var/ccpd/fifo0 -E
cd /usr/share/ppd
sudo ln -s /usr/share/cups/model/CNCUPSLBP1210CAPTJ.ppd


at this point there is one command on the original howto that I did not follow
yet my printer works. the command was listed as follows for those who are
curious (or who's installation fails(??)); 
sudo /usr/sbin/ccpdadmin -p LBP1210 -o /dev/usblp0



step 9:


we will now edit the ccpd script and backup the original one. issue the following commands
in your terminal;

sudo mv /etc/init.d/ccpd ccpdold
sudo gedit /etc/init.d/ccpd

copy and paste the following text into the gedit window;

#!/bin/sh
#
# ccpd          startup script for Canon Printer Daemon for CUPS
#
#               Modified for Debian GNU/Linux
#               by Raphael Doursenaud <rdoursenaud@free.fr>.

DAEMON=/usr/sbin/ccpd
LOCKFILE=/var/lock/subsys/ccpd
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
NAME=ccpd
DESC="Canon Printer Daemon for CUPS"

test -f $DAEMON || exit 0

case $1 in
  start)
        echo -n "Starting $DESC: $NAME"
        start-stop-daemon --start --quiet --exec $DAEMON
        echo "."
        ;;
  stop)
        echo -n "Stopping $DESC: $NAME"
        start-stop-daemon --stop --quiet --oknodo --exec $DAEMON
        echo "."
        ;;
  status)
        echo "$DESC: $NAME:" `pidof $NAME`
        ;;
  restart)
        echo -n "Restarting $DESC: $NAME"
        start-stop-daemon --stop --quiet --oknodo --exec $DAEMON
        sleep 1
        start-stop-daemon --start --quiet --exec $DAEMON
        echo "."
        ;;
  *)
        echo "Usage: ccpd {start|stop|status}"
        exit 1
        ;;
esac

exit 0


(the above script was taken from [http://rdoursenaud.free.fr/debian/capt.html](http://rdoursenaud.free.fr/debian/capt.html) and appears
as part of the original howto at help.ubuntu.com)

save the file and close gedit.

issue the following command in your terminal to give execution rights to the script file;

sudo chmod a+x /etc/init.d/ccpd



step 10:

we now start the ccpd daemon and set it to start automatically when the system starts. 
issue the following commands in your terminal;

sudo /etc/init.d/ccpd start
sudo update-rc.d ccpd defaults 20


step 11:

we need to add 2 lines to our usr.sbin.cupsd file. issue the following command in
your terminal;

sudo gedit /etc/apparmor.d/usr.sbin.cupsd

now we need to scroll down to find the following section;

/var/run/avahi-daemon/socket rw,
/var/run/cups/ rw,
/var/run/cups/** rw,
/var/spool/cups/ rw,
/var/spool/cups/** rw,

underneath those lines we add the following 2 lines;

# needed for Canon CAPT driver
/var/ccpd/** rw,

now it should look like this;

/var/run/avahi-daemon/socket rw,
/var/run/cups/ rw,
/var/run/cups/** rw,
/var/spool/cups/ rw,
/var/spool/cups/** rw,
# needed for Canon CAPT driver
/var/ccpd/** rw,

save the file and close gedit.

then we issue the following command in the terminal;

sudo /etc/init.d/apparmor restart


step 12:

turn off your printer and reboot your system. 


step 13:

After your system has restarted and you are logged in, turn your printer back on.

You may receive a message from gnome saying that it has installed your LBP-1210 using
LBP-1100 drivers. Ignore this message and do nothing about it.

We will now check our installation by issuing the following command at the terminal;

sudo ccpdadmin

the output from ccpdadmin should look like this;

Usage: 
  ccpdadmin [-p Printer-name -o Printer-dev-path]
  ccpdadmin [-x Remove-Printer-name]


 CUPS_ConfigPath = /etc/cups/
 LOG Path        = None
 UI Port         = 39787

 Entry Num  : Spooler   : Backend       : FIFO path             : Device Path  : Status 
 ----------------------------------------------------------------------------
     [0]    : LBP1210   : ccp           : /var/ccpd/fifo0       : /dev/usblp0  :


Now issue the following command in your terminal;

captstatusui -P LBP1210

this should bring up a window which after a short time will say "Ready to print"


step 14:

The installation is complete. You might find that there is a lengthy delay between sending
a job to the printer, and the printing actually taking place but never fear, the printing
will come out after some seconds and the printing will be be beautiful =o)

---

### Post by K.Mandla on 2008-01-22
Moved to Hardware and Laptops.

---

