---
title: "All Cannon Printer Driver (LBP3200)"
date: 2009-11-05
forum: Hardware
---

### Post by rajamohan on 2009-11-05
This article describe installing cannon CAPT driver by compiling from source

The details ment here are for 64Bit Ubuntu 9.10 System Karmic Kola and LBP3200 printer. I had complied this article from the reference below

If Possible switch Off the Printer until we complete installation of driver this may avoid auto installation of the driver after we complete the steps.

Ref 1: [html]http://ubuntuforums.org/showpost.php?p=6134355&postcount=2[/html]Ref 2: [html]https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900#Compiling%20the%20driver%20%28amd64%29%20Steps:[/html]Use Case

   1. Compile Cannon Driver from latest source
   2. Install Compiled Driver
   3. Automate loading the CAPT demon 

Files to Download

Cannon Linux Printer Driver (CAPT) Source [html]http://support-au.canon.com.au/contents/AU/EN/0900772411.html[/html]libcupsys2.deb [html]http://packages.ubuntu.com/jaunty-updates/all/libcupsys2/download[/html]This is a dummy package installing it will solve dependancy issue installing capt-common package

Note: Deb Packages can be directly installed by right clicking it and selecting option open with “GDebi Package Installer”

Step1 - Installing the Required packages to compile the driver

Install following packages before start compiling (Some Package may report already installed such case leave as such and contiune installing others)

Install Debian package development tools
Install libcupsys2 Download the deb from here [html]http://packages.ubuntu.com/jaunty-updates/all/libcupsys2/download[/html]Install The GNU Standard C++ Library v3 (development files)
Install helper programs for debian/rules
Install automatic configure script builder
Install Development files for the GLib library
Install Development files for the GTK+ library
Install A system independent dlopen wrapper for GNU libtool
Install library for common error values and messages in GnuPG components
Install Common UNIX Printing System(tm) - Development files CUPS library
Install Development files for the GNOME XML library

> 
sudo apt-get install build-essential
sudo apt-get install libstdc++6-4.4-dev
sudo apt-get install debhelper
sudo apt-get install autoconf
sudo apt-get install libglib2.0-dev
sudo apt-get install libgtk2.0-dev
sudo apt-get install libltdl-dev
sudo apt-get install libgpg-error-dev
sudo apt-get install libcups2-dev
sudo apt-get install libxml2-dev
Step2 – Unpacking the Source

> 
tar xfz CAPT_Printer_Driver_for_Linux_Src_V190_uk_EN.tar.gz
cd CAPT_Printer_Driver_for_Linux_Src_V190_uk_EN/Src/
tar xfz cndrvcups-common-1.90-1.tar.gz 
tar xfz cndrvcups-capt-1.90-1.tar.gz
Step3 – Compiling cndrvcups-common-1.90-1

> 
cd cndrvcups-common-1.90
gedit ./debian/control 
Change “Architecture: i386” to “Architecture: amd64” save and close editor

> 
dpkg-buildpackage
The debian package cndrvcups-common_1.90-1_amd64.deb will be placed in CAPT_Printer_Driver_for_Linux_Src_V190_uk_EN/Src

Step4 – Installing cndrvcups-common_1.90-1_amd64.deb

This package need to be installed before starting the next step compiling the cndrvcups-capt source depends some library from cndrvcups-common

> 
cd ..
sudo dpkg -i cndrvcups-common_1.90-1_amd64.deb
Step5 – Compiling & Installing cndrvcups-capt-1.90-1

> 
cd cndrvcups-common-1.90
gedit ./debian/control
Change “Architecture: i386” to “Architecture: amd64” save and close editor

> 
gedit ./debian/rules
Comment the option dh_shlibdeps by adding “#” at the start of the line It should look like as below after editing 
```

#     dh_shlibdeps

```save and close editor

> 
dpkg-buildpackage
The debian package cndrvcups-capt_1.90-1_amd64.deb will be placed in CAPT_Printer_Driver_for_Linux_Src_V190_uk_EN/Src

> 
sudo dpkg -i cndrvcups-capt_1.90-1_amd64.deb
Now our cannon driver is installed and ready to configure

Step6 – Editing the startup script for starting CAPT daemon

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

> 
cd /etc/init.d 
sudo cp ccpd ccpd-old 
sudo gedit ccpd 
delete all existing content and replace with the above script, save and close the editor

Step7 – Setting the printer for CUPS

> 
sudo /etc/init.d/cups restart 
sudo /usr/sbin/lpadmin -p LBP3200 -P /usr/share/cups/model/CNCUPSLBP3200CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
This will add printer LBP3200

Step8 – Setting the printer for CAPT

> 
sudo /usr/sbin/ccpdadmin -p LBP3200 -o /dev/usb/lp0
This will add printer LBP3200 to the CAPT monitor (daemon)

Step9 – Automating CAPT while booting the system

> 
sudo update-rc.d ccpd defaults 50
Edit*
We are using 50 which means the ccpd is one the the last daemons to start This point is noted by _TommyBoy_

Step10 – Finalisation

Now we are done all setting now its time to switch on our printer. Connect your printer and power on. As soon as the printer is connected Ubuntu auto install a new driver for our printer and make it as default printer.

Now our final step is to chage our set printer to default and disable the auto installed printer (Note: do not delete the printer auto installed by Ubuntu, since Ubuntu will reinstall the printer again after a restart so its better to disable it or leave it as is)

Steps to change default Printer

Select
> System->Administrator->PrintingThis will list all the printer installed, right click the printer named LBP3200 and select (click) Set Us Default

Right click the auto installed printer by Ubuntu (LBP3200-2) and uncheck Enabled.

Now we are complete Lets Restart the computer.

“Success“ our printer is now ready to print, “Happy Computing”

I thank the community by creating this thread :D

---

### Post by Fitmoos on 2010-01-01
I worked, after intentdo a year, read this 
guide and finally works. But I use i386 eee901, 
Ubuntu 9.10, and I modified the guidance for these 
computers. Sorry, I do not speak English, so does the 
XD translator.

Me funciono, despues de haber intentdo un año, leo esta 
guia y finalmente funciona. Pero yo uso i386, eee901 (xubuntu), 
ubuntu 9.10, y he modificado la guia para este tipo de 
computadores. Lo siento, no hablo ingles, lo hace el 
traductor XD.

[QUOTE=howto:lbp3200 in 9.10 i386]This article describe installing cannon CAPT driver by compiling from source

The details ment here are for 64Bit Ubuntu 9.10 System Karmic Kola and LBP3200 printer. I had complied this article from the reference below

If Possible switch Off the Printer until we complete installation of driver this may avoid auto installation of the driver after we complete the steps.

Ref 1: [html]http://ubuntuforums.org/showpost.php?p=6134355&postcount=2[/html]Ref 2: [html]https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900#Compiling%20the%20driver%20%28amd64%29%20Steps:[/html]Use Case

   1. Compile Cannon Driver from latest source
   2. Install Compiled Driver
   3. Automate loading the CAPT demon 

Files to Download

Cannon Linux Printer Driver (CAPT) Source [html]http://support-au.canon.com.au/contents/AU/EN/0900772411.html[/html]libcupsys2.deb [html]http://packages.ubuntu.com/jaunty-updates/all/libcupsys2/download[/html]This is a dummy package installing it will solve dependancy issue installing capt-common package
[http://packages.debian.org/search?keywords=libstdc%2B%2B5](http://packages.debian.org/search?keywords=libstdc%2B%2B5)

Note: Deb Packages can be directly installed by right clicking it and selecting option open with “GDebi Package Installer”

Step1 - Installing the Required packages to compile the driver

Install following packages before start compiling (Some Package may report already installed such case leave as such and contiune installing others)

Install Debian package development tools
Install libcupsys2 Download the deb from here 
Install cndrvcups-common_1.90-1_i386.deb
Install libstdc++5-3.3-dbg.deb (download here [http://packages.debian.org/search?keywords=libstdc%2B%2B5](http://packages.debian.org/search?keywords=libstdc%2B%2B5))
Install cndrvcups-capt_1.90-1_i386.deb
[html]http://packages.ubuntu.com/jaunty-updates/all/libcupsys2/download[/html]Install The GNU Standard C++ Library v3 (development files)
Install helper programs for debian/rules
Install automatic configure script builder
Install Development files for the GLib library
Install Development files for the GTK+ library
Install A system independent dlopen wrapper for GNU libtool
Install library for common error values and messages in GnuPG components
Install Common UNIX Printing System(tm) - Development files CUPS library
Install Development files for the GNOME XML library

Step2 – unnesesary for i686 (or i386)

Step3 – unnesesary for i686

Step4 – unnesesary for i686

Step5 – unnesesary for i686

Step6 – Editing the startup script for starting CAPT daemon

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

Step7 – Setting the printer for CUPS

This will add printer LBP3200

Step8 – Setting the printer for CAPT

This will add printer LBP3200 to the CAPT monitor (daemon)

Step9 – Automating CAPT while booting the system

Edit*
We are using 50 which means the ccpd is one the the last daemons to start This point is noted by _TommyBoy_

Step10 – Finalisation

Now we are done all setting now its time to switch on our printer. Connect your printer and power on. As soon as the printer is connected Ubuntu auto install a new driver for our printer and make it as default printer.

Now our final step is to chage our set printer to default and disable the auto installed printer (Note: do not delete the printer auto installed by Ubuntu, since Ubuntu will reinstall the printer again after a restart so its better to disable it or leave it as is)

Steps to change default Printer

Select
This will list all the printer installed, right click the printer named LBP3200 and select (click) Set Us Default

Right click the auto installed printer by Ubuntu (LBP3200-2) and uncheck Enabled.

Now we are complete Lets Restart the computer.

“Success“ our printer is now ready to print, “Happy Computing”

I thank the community by creating this thread :D[/QUOTE]


Gracias, al fin puedo imprimir en mi computador:popcorn::popcorn::popcorn::popcorn::popcorn:

---

### Post by nam66 on 2010-01-11
Hello there,
I'm still new in linux. Currently i try to install canon LBP7200Cd to my Ubuntu 64bit system.

I try to follow your step above but then I stuck here
> 
Step5 – Compiling & Installing cndrvcups-capt-1.90-1

Quote:
cd [COLOR="Red"]cndrvcups-common-1.90[/COLOR]
gedit ./debian/control
Change “Architecture: i386” to “Architecture: amd64” save and close editor

Quote:
gedit ./debian/rules
Comment the option dh_shlibdeps by adding “#” at the start of the line It should look like as below after editing 
Code:
#     dh_shlibdeps
save and close editor

Quote:
dpkg-buildpackage

I'm sure that the red one should be "cd cndrvcups-capt-1.90"
but then, when i try to "sudo dpkg-buildpackage" command,

i got this error
> mkdir -p /home/shilajarkoni/CAPT_Printer_Driver_for_Linux_Src_V190_uk_EN/Src/cndrvcups-capt-1.90/debian/cndrvcups-capt/usr/share/doc/cndrvcups-capt
install *capt*.txt /home/shilajarkoni/CAPT_Printer_Driver_for_Linux_Src_V190_uk_EN/Src/cndrvcups-capt-1.90/debian/cndrvcups-capt/usr/share/doc/cndrvcups-capt
dh_testdir
dh_testroot
dh_installchangelogs 
dh_installdocs
dh_installexamples
dh_installman
dh_link
dh_strip
dh_compress
dh_fixperms
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: error: couldn't find library libstdc++.so.5 needed by debian/cndrvcups-capt/usr/bin/captmoncnaba (ELF format: 'elf32-i386'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make: *** [binary-arch] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2


I already have libstdc++.so.5 in /usr/lib folder, I install this from here 
> Install libstdc++5-3.3-dbg.deb (download here [http://packages.debian.org/search?ke...libstdc%2B%2B5](http://packages.debian.org/search?ke...libstdc%2B%2B5))

that being given above...

so hopefully someone can figure this thing out...I thought the dpkg problem, so I update it with 1.5version but still got same error..

Hope to here from all of you soon... Really need help here

---

### Post by rajamohan on 2010-04-04
Hi Friends,

There is a latest driver release for Cannon CAPT driver which solve many issues and support more device, download the driver from the below link

[http://support-au.canon.com.au/contents/AU/EN/0900772408.html](http://support-au.canon.com.au/contents/AU/EN/0900772408.html)

For 32 bit system there is a pre compiled deb files, you have a detailed document under doc folder, when you extract the downloaded files.

For compiling you can follow the same instruction as I mentioned above

Rajamohan

---

### Post by tropdoug on 2010-06-01
Just worked my way through this excellent tutorial for my LBP3200 on lucid 10.04 64Bit.

all went well until```
cd /etc/init.d 
sudo cp ccpd ccpd-old 
sudo gedit ccpd                       
```then I found out that 10.04 does not have a /etc/init.d/ccpd file?? So ithought well might as well create one, so I did and saved it with the new script in it. The next error was ```
sudo /usr/sbin/ccpdadmin -p LBP3200 -o /dev/usb/lp0                      
``` came up with Error no such file

Not knowing what the content of that file should be meant I could not create one. So I persisted and comnpleted step 9. Step 10 though did not install a new printer other than the one that the system installed which is the one we want to disable. 

So - any suggestions for the end part of this otherwise good tut?

I really need that printer now.

---

### Post by Fitmoos on 2010-07-03
here easy solution for lbp 3200

[http://ubuntu-utah.ubuntuforums.org/showthread.php?p=9544723#post9544723](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=9544723#post9544723)

---

