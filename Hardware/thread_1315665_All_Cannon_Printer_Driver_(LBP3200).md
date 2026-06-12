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

Note: Deb Packages can be directly installed by right clicking it and selecting option open with &#8220;GDebi Package Installer&#8221;

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
Step2 &#8211; Unpacking the Source

> 
tar xfz CAPT_Printer_Driver_for_Linux_Src_V190_uk_EN.tar.gz
cd CAPT_Printer_Driver_for_Linux_Src_V190_uk_EN/Src/
tar xfz cndrvcups-common-1.90-1.tar.gz 
tar xfz cndrvcups-capt-1.90-1.tar.gz
Step3 &#8211; Compiling cndrvcups-common-1.90-1

> 
cd cndrvcups-common-1.90
gedit ./debian/control 
Change &#8220;Architecture: i386&#8221; to &#8220;Architecture: amd64&#8221; save and close editor

> 
dpkg-buildpackage
The debian package cndrvcups-common_1.90-1_amd64.deb will be placed in CAPT_Printer_Driver_for_Linux_Src_V190_uk_EN/Src

Step4 &#8211; Installing cndrvcups-common_1.90-1_amd64.deb

This package need to be installed before starting the next step compiling the cndrvcups-capt source depends some library from cndrvcups-common

> 
cd ..
sudo dpkg -i cndrvcups-common_1.90-1_amd64.deb
Step5 &#8211; Compiling & Installing cndrvcups-capt-1.90-1

> 
cd cndrvcups-capt-1.90
gedit ./debian/control
Change &#8220;Architecture: i386&#8221; to &#8220;Architecture: amd64&#8221; save and close editor

> 
gedit ./debian/rules
Comment the option dh_shlibdeps by adding &#8220;#&#8221; at the start of the line It should look like as below after editing 
```

#     dh_shlibdeps

```save and close editor

> 
dpkg-buildpackage
The debian package cndrvcups-capt_1.90-1_amd64.deb will be placed in CAPT_Printer_Driver_for_Linux_Src_V190_uk_EN/Src

> 
sudo dpkg -i cndrvcups-capt_1.90-1_amd64.deb
Now our cannon driver is installed and ready to configure

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

> 
cd /etc/init.d 
sudo cp ccpd ccpd-old 
sudo gedit ccpd 
delete all existing content and replace with the above script, save and close the editor

Step7 &#8211; Setting the printer for CUPS

> 
sudo /etc/init.d/cups restart 
sudo /usr/sbin/lpadmin -p LBP3200 -P /usr/share/cups/model/CNCUPSLBP3200CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
This will add printer LBP3200

Step8 &#8211; Setting the printer for CAPT

> 
sudo /usr/sbin/ccpdadmin -p LBP3200 -o /dev/usb/lp0
This will add printer LBP3200 to the CAPT monitor (daemon)

Step9 &#8211; Automating CAPT while booting the system

> 
sudo update-rc.d ccpd defaults 50

Edit*
We are using 50 which means the ccpd is one the the last daemons to start This point is noted by _notlistening_, _TommyBoy_


Step10 &#8211; Finalisation

Now we are done all setting now its time to switch on our printer. Connect your printer and power on. As soon as the printer is connected Ubuntu auto install a new driver for our printer and make it as default printer.

Now our final step is to chage our set printer to default and disable the auto installed printer (Note: do not delete the printer auto installed by Ubuntu, since Ubuntu will reinstall the printer again after a restart so its better to disable it or leave it as is)

Steps to change default Printer

Select
> System->Administrator->PrintingThis will list all the printer installed, right click the printer named LBP3200 and select (click) Set Us Default

Right click the auto installed printer by Ubuntu (LBP3200-2) and uncheck Enabled.

Now we are complete Lets Restart the computer.

&#8220;Success&#8220; our printer is now ready to print, &#8220;Happy Computing&#8221; :D

I thank the community by creating this thread

---

### Post by notlistening on 2009-11-05
This line causes me issues:

```
sudo update-rc.d ccpd defaults 20 
```I had to modify this for Karmic to stop ccpd from not starting correctly at boot and using 100% of one CPU :

```
sudo update-rc.d ccpd defaults 50
```Jaunty was another story found here:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/LBP3010](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/LBP3010)

---

### Post by rajamohan on 2009-11-06
[quote=notlistening;8252343]This line causes me issues:

```
sudo update-rc.d ccpd defaults 20 
```I had to modify this for Karmic to stop ccpd from not starting correctly at boot and using 100% of one CPU :

```
sudo update-rc.d ccpd defaults 50
```Thanks _notlistening,_ I had updated the content as pointed by you

---

### Post by Claritux on 2009-11-08
I'm trying to apply this for the LBP5050 by following this guide (of course, using "LBP5050" instead of "LBP3200" in the commands). The setup worked fine for me, I've followed the whole guide without problems, but when I run ```
captstatusui -P LBP5050
``` I get an error saying "Check the DevicePath of /etc/ccpd.conf" and I'm not able to print. Any solution to this?

---

### Post by Claritux on 2009-11-08
BTW, here's my /etc/ccpd.conf

```

# Canon Printer Daemon for CUPS Configuration Data

<Path>
# CUPS configuration file path.
#  Default  /etc/cups/

CUPS_ConfigPath   /etc/cups/

# Log directory path.
#  LogDirectoryPath /var/log/CCPD/

</Path>

# Printer entries.
#  Mapping each "Printer Name" to each "Printer Device Port".
#  The "Printer Name" has to be identical to the CUPS printer queue name.
#  
#  For example, if you prepare a printer named "LBP3200" as a CUPS printer
#  queue name, and the printer is connected to the USB port "/dev/usb/lp0",
#  you can use the following three lines example just by removing the
#  comment symbol "#" of each line.
#<Printer  LBP3200>
#DevicePath  /dev/usb/lp0
#</Printer>

<Printer LBP5050>
DevicePath /dev/usb/lp0
</Printer>

<Ports>
# Status monitoring socket port.
#  Default 59787
UI_Port  59787
</Ports>
```

---

### Post by spodesabode on 2009-11-09
Just trying this now.

FYI - the link to the Canon Source should be :

[http://support-au.canon.com.au/contents/AU/EN/0900772502.html](http://support-au.canon.com.au/contents/AU/EN/0900772502.html)

The one you have is for the pre-compiled driver.

Interestingly - the UK support page doesn't have 1.9 - only 1.8!

UPDATE:

Yes, this worked a charm. Although in reality - I think all I needed was the new version 1.9 drivers - as I'm on 32Bit - I'm not sure I needed to compile from source...

---

### Post by rajamohan on 2009-11-10
Dear akshov,

If all went well, the issue might due to auto detected printer driver, please check you had done the last step, setting the default printer, and also check if there is any printjob pending in the auto detect printer, I had this issue when I had a printjob in the auto select printer and every time I switch on the printer.

Hope this solve your issue

Rajamohan

---

### Post by bayvista on 2009-11-17
Hi,

I have found the DOC for installing the drivers, but is online (HTML) When I try to print it, all I get is the first page. Do you know how to print the whole Users Guide? I am using Firefox.

---

### Post by kyosti.huhtala on 2010-01-06
I have LBP5050 with Ubuntu 9.10 on an AMD64.system. I think I have closely followed the instructions above but still with no success.

A simple 3 lines ascii files stays in queue with status "processing". If I abort it, the properties window shows "Can't open FIFO: Interrupted system call".

Any suggestions?

---

### Post by merlyn on 2010-01-25
Mate, I've given up on Ubuntu these days and moved over pure Debian.

But for the life of me could I get my printer working?

When using Ubuntu in the past I used a much older more complicated Howto, that never failed me until recently.  

Your guide along with the input of others is so much better presented, less steps, and works.

Cheers.

---

### Post by eastman75 on 2010-01-25
Hi rajamohan,
Very nicely and clearly put is your message. A lot of thanks!
I've tried to install the compiled 1.90 version to work with Canon LBP-810 but failed to print. Is it possible that the newest driver version doesn't support old Canon models (such as mine) any more? Shall I try, say, version 1.60 or 1.80?
Please find the time to answer. All the gratefullness in advance...

---

### Post by rajamohan on 2010-04-04
Hi Friends,

There is a latest driver release for Cannon CAPT driver which solve many issues and support more device, download the driver from the below link

[http://support-au.canon.com.au/contents/AU/EN/0900772408.html](http://support-au.canon.com.au/contents/AU/EN/0900772408.html)

For 32 bit system there is a pre compiled deb files, you have a detailed document under doc folder, when you extract the downloaded files.

For compiling you can follow the same instruction as I mentioned above

Rajamohan

---

### Post by bayvista on 2010-05-10
I have installed the latest driver v2.0 with Lucid. It sort of works, but I have to jiggle things after each reboot to get the printer (LBP3100) to print. Not really sure what the problem is. I have done everything suggested. It seems to be related to starting CCPD. I have added to 'Startup Applications'.

Any ideas?

Solved. My problem was that the printer driver is called LPB3150, not 3100. I uninstalled and reinstalled with the correct names and all seems to work now,

---

### Post by tsouliang on 2010-09-22
Hello ;)

Thanks,
There is a mistake here :
> Step5 – Compiling & Installing cndrvcups-capt-1.90-1

 	Quote:
 	 	 		 			 				cd cndrvcups-common-1.90

You speak about cndrvcups-capt but in the command you write cndrvcups-common ...

Just a little error but can make all wrong ;)

bye !

---

### Post by tsouliang on 2010-09-22
and for me, all go right, but in fine, nothing print ...
I'm on lucid, with amd64.

The printer see the task, work in progress ... but nothing.
When i try to print a page, in the panel  for the print selection, there is the error "ccp_send data error, exit"

Please, sorry my English, i'm French ;)

---

### Post by rajamohan on 2010-09-22
Hi tsouliang, thanks for taking time to notify the issue,I had fixed the statement. ya its really misleading command

> **tsouliang said:**
> Hello ;)

Thanks,
There is a mistake here :


You speak about cndrvcups-capt but in the command you write cndrvcups-common ...

Just a little error but can make all wrong ;)

bye !

---

### Post by rajamohan on 2010-09-22
Hi tsouliang,

There are some assumption here related to hardware, it is assumed you have only one usb printer connected to the computer so the device is represented like this /dev/usb/lp0

If you have more than one usb printer (or alike) connected find the correct device (it may be /dev/usb/lp1, ..lp2 and so on) and use it in the step 8.

If you have parallel port interface u need to use /dev/parport0 in the step 8.

Hope this help,

Step8 – Setting the printer for CAPT

Quote:
sudo /usr/sbin/ccpdadmin -p LBP3200 -o /dev/usb/lp0

Regards
Rajamohan

> **tsouliang said:**
> and for me, all go right, but in fine, nothing print ...
I'm on lucid, with amd64.

The printer see the task, work in progress ... but nothing.
When i try to print a page, in the panel  for the print selection, there is the error "ccp_send data error, exit"

Please, sorry my English, i'm French ;)

---

### Post by tsouliang on 2010-09-22
Thanks for the help ;)
But i have only one printer ( at the same time ) on usb, and in "/dev/usb", just lp0 ...

I realy don't understand what go wrong :(

---

### Post by toto1234 on 2010-10-29
Hi,
Thanks for this tutorial, which helped me to install the last driver for my Canon printer.

  + driver installed : CAPT_Printer_Driver_for_Linux_V200_uk_EN.tar.gz
  + OS : Debian Squeeze (this changes some details)

Here are some suggestions of corrections :

  0) The package ia32-libs MUST be installed. The package gs-esp may be installed too.

  1) I had no need to install libcupsys2 package

  2) Step 3 : also need to change the dependency 'cupsys' into 'cups', because the package cupsys no longer exists in Debian Squeeze

  3) Step 6 : The file /etc/init.d/ccpd must include the following lines (for example after the 3 first commented lines) :
### BEGIN INIT INFO
# Provides:          ccpd
# Required-Start:    $local_fs $remote_fs $syslog $network $named
# Should-Start:      $ALL
# Required-Stop:     $syslog $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Description:       Start Canon Printer Daemon for CUPS
### END INIT INFO

  4) Step 7 : the command looks like this :
sudo /usr/sbin/lpadmin -p LBP2900 -P /usr/share/cups/model/CNCUPSLBP2900CAPTK.ppd -v ccp://localhost:55017 -E

  5) Step 9 : update-rc won't work and the better command is :
insserv ccpd
  (with eventually before : rm /etc/rc?.d/[KS]??ccpd )

That's all for my participation. Sorry if the text isn't well formatted since it's my first post.
Again, the tutorial was great !

---

### Post by prkos on 2010-12-15
Thank you for the tutorial! I do have some problems though. I followed all the steps but when trying to print a test page I get the "ccp_send data error, exit" error. 

I found the script that does things automatically and tried it [http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu](http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu) After reboot I'm not getting the "ccp_send data error, exit" message any more, but still printing doesn't work. 

I fiddled with the Device URI: field, chose USB one and after this choice when I try to print the test page I get "Idle - Printer is now online. " The task is marked as Processing then it disappears from the jobs list. In the log it's marked as Completed. 

The ubuntu recognized printer is disabled, and the LBP3250 is set as default and enabled, but sometimes when I come back to Printer configuration it's disabled. 

What might be wrong?

---

### Post by condamine on 2010-12-28
Thanks for this fine tutorial!

If you are contemplating purchasing one of these CAPT printers, my advice is: [COLOR="Red"]DON'T[/COLOR].

CAPT (Canon Advanced Printing Technology) printers are [Windows GDI]("http://en.wikipedia.org/wiki/Graphics_Device_Interface") printers: which means they have no rendering capability; this is all done on the host computer. Remember how terrible [COLOR="Red"]winmodems[/COLOR] were, well these are [COLOR="Red"]winprinters[/COLOR] - just as problematic! [Further advice not to purchase these paperweights]("http://www.openprinting.org/printer/Generic/Generic-GDI_Printer")

Although Canon produces the CAPT drivers for these GDI based printers they offer no support at all. This is clearly stated in the terms stated on the download page for the CUPS CAPT drivers
> "Canon Printers", and Canon local company as selling agency of Canon Printers, do not receive any user support call and /or request or any requests for information about the Software and Related Information.

OK now that I've got that disclaimer out of the way I can confirm, after lots of trial and error, that a LBP3100B can print under Ubuntu. If you have a 32bit system just following the Installation instructions Canon supplies should have you up and running fairly quickly.

I have managed to set-up a working shared printer (LBP3100B) on a 32bit Lucid Lynx (Ubuntu 10.04) desktop.

I didn't have any luck compiling the 64Bit drivers.

I haven't tried any of the other printers, but I expect all of the supported printers will work OK under Ubuntu. Here is the list of supported printers, from the installation documents that come with the [driver download]("http://support-au.canon.com.au/contents/AU/EN/0900772408.html")
> LBP9100Cdn
LBP7200C series
LBP5050 series
LBP3010/LBP3018/LBP3050
LBP3100/LBP3108/LBP3150
LBP3250
LBP3310
LBP5100
LBP5300
LBP3500
LBP3300
LBP5000
LBP3210
LBP3000
LBP2900
LBP3200
LBP-1120
LBP-1210


My questions/comments are as follows:

*Step6 – Editing the start-up script for starting CAPT daemon*
I found that there are several different modified ccpd start-up scripts to be found on the net. I decided the original supplied by Canon was too confusing to follow. This is the ccpd start-up script I decided to use...
```

#!/bin/sh
# startup script for Canon Printer Daemon for CUPS (ccpd)
# Modified for Debian GNU/Linux
# Based on a compile for 64 bit instructions by rajamohan
#   	Ubuntu Forums > The Ubuntu Forum Community > Main Support Categories > Hardware & Laptops > [SOLVED] All Cannon Printer Driver (LBP3200) 
# http://ubuntuforums.org/showthread.php?t=1315665

##Use the update.rc.d runlevel defaults
### BEGIN INIT INFO
# Provides:         ccpd
# Required-Start:   $local_fs $remote_fs $syslog $network $named
# Should-Start:     $ALL
# Required-Stop:    $syslog $remote_fs
# Default-Start:    2 3 4 5
# Default-Stop:     0 1 6
# Description:      Start Canon Printer Daemon for CUPS
### END INIT INFO

#Decided not to export path
DAEMON=/usr/sbin/ccpd
LOCKFILE=/var/lock/subsys/ccpd
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
NAME=ccpd
DESC="Canon Printer Daemon for CUPS"

test -f $DAEMON || exit 0

. /lib/lsb/init-functions


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

```

*Step7 – Setting the printer for CUPS*
I decided not to deviate from the Canon instructions, Canon's lpadmin command worked for me, however, [COLOR="Red"]BEWARE[/COLOR] of the typo in the Canon instructions! [COLOR="Red"]–[/COLOR]E should be [COLOR="Red"]-[/COLOR]E
```
sudo /usr/sbin/lpadmin -p LBP3100 -m CNCUPSLBP3150CAPTK.ppd -v ccp://localhost:59687 -E

```

*Step8 – Setting the printer for CAPT*
I found that the lpr.log & debug log make this comment....
> udev-configure-printer: Consider also queues with "/usb/lp0*" or "USBlp0" in their URIs as matching
This is due to the auto detection of the printer mentioned in *Step10 – Finalisation*. Does anyone know how this can be turned off? :frown:

*Re: Step9 – Automating CAPT while booting the system*
**Automatic starting CAPT daemon (CCPD start-up) issues**
[COLOR="Green"]rajamohan[/COLOR]: in your modified ccpd start-up script I see you have included some logging capability. Could you please advise where this logged information ends up? 	:-?
[COLOR="Green"]toto1234[/COLOR]: I see you have changed the LSB init script header provided by Canon in their read-me file included with the driver download.
> # Default-Start:     3 5
# Default-Stop:      0 1 2 6

to the default and much more sensible
> # Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
But when I ran ```
sudo insserv ccpd
``` I ended up with a page full of errors culminating in > insserv: exiting now without changing boot order!
So I reverted to this update-rc.d command
```
sudo update-rc.d ccpd start 50 2 3 4 5 . stop 80 0 1 6 .
```
which is the default for the start and stop runlevels. I decided to use the same sequence as CUPS (eg: starting init sequence of 50 and a stop sequence of 80).

:confused: Sorry to labour on about automatically starting CCPD but with all the different init mechanisms I got terribly confused and sidetracked. Here is a list of the man pages that I consulted!

```
init (5)       - Upstart init daemon job configuration
upstart (7)          - Upstart process management daemon
init (8)             - Upstart process management daemon
initctl (8)          - init daemon control tool
inittab (5)          - init daemon configuration
insserv (8)          - Enable an installed system init script
service (8)          - run a System V init script
start (8)            - init daemon control tool
status (8)           - init daemon control tool
stop (8)             - init daemon control tool
```

Some final comments:
It is very confusing as there are multiple methods of setting up printers. There is the cups admin pages via [http://localhost:631](http://localhost:631), the Ubuntu tool under System > Administration > Printing and then the command line tools mentioned in this tutorial as well as the various *.conf files involved.

After my initial set up I was not getting any error messages and the printer status was OK at idle, but nothing printed. Using the Cups Modify Printer web interface and Turning off "Share this Printer" allowed my first print job.

I found an occasional reboot of the computer and printer would fix the strange problems that occurred while trying to set up CUPS, CAPT, Ghostscript, SAMBA & UFW - Be warned, there are a lot of complicated bits of software involved in getting these winprint beasts working - expect a lot of this 	](*,)

---

### Post by prkos on 2011-01-04
I haven't tried fixing it on ubuntu, but I was able to make the printer work on fedora 14. 

At first I followed the instructions from the driver doc to install the driver on fedora, but it wouldn't work there either, the same as ubuntu. 

Then I found a tutorial that includes one extra step - stopping Haldaemon, and this installation went ok, and I can now print on fedora 14 with LBP3250. 

[http://forums.fedoraforum.org/showthread.php?t=256926](http://forums.fedoraforum.org/showthread.php?t=256926)

---

### Post by rajamohan on 2011-11-06
OK now ubuntu 11.10 is out so I thought of updating this thread for the latest version and most recent driver. This time I am going to details the installation of the driver from the existing build direct from the Canon linux driver, below are the steps :)

1. Download the driver from the link [http://support-au.canon.com.au/contents/AU/EN/0900772408.html](http://support-au.canon.com.au/contents/AU/EN/0900772408.html)
2. unzip the downloaded driver assuming you had downloaded to the default folder (Downloads)

    > cd Downloads
    tar xfz Linux_CAPT_PrinterDriver_V230_uk_EN.tar.gz3. This will create a folder "Linux_CAPT_PrinterDriver_V230_uk_EN" in the current directory. You will have four folders inside this, of which we are concerned about two folder i.e "32-bit_Driver" and "64-bit_Driver"

4. Ubuntu 11.10 have a missing package gs-esp so we need to fix that download the .deb package from the link and install it [http://launchpadlibrarian.net/62641639/gs-esp_9.01%7Edfsg%7Esvn12047-0ubuntu1_all.deb]("http://launchpadlibrarian.net/62641639/gs-esp_9.01%7Edfsg%7Esvn12047-0ubuntu1_all.deb")

    > sduo dpkg -i gs-esp_9.01~dfsg~svn12047-0ubuntu1_all.debFor 32 Bit System

5. change to folder "32-bit_Driver"

    > cd Linux_CAPT_PrinterDriver_V230_uk_EN/32-bit_Driver/Debian
    sudo dpkg -i cndrvcups-common_2.30-1_i386.deb
    sudo dpkg -i cndrvcups-capt_2.30-1_i386.debFor 64 Bit System

The driver file contain only contain RPM files so we need to convert it to .deb files, for this we will install a alien package which is a tool to convert RPM to DEB

    > sudo apt-get install alienNow we need to convert the rpm files (assuming we are in Downloads Folder)

    > cd Linux_CAPT_PrinterDriver_V230_uk_EN/62-bit_Driver/RPM
    sudo alien *.rpm5. now we have the .deb files we can install the driver

    > sudo dpkg -i cndrvcups-common_2.30-1_amd64.deb
    sudo dpkg -i cndrvcups-capt_2.30-1_amd64.debLet start prepare to start configuring the printer.

6. Ubuntu 11.10 had blacklisted usblp modules (I am not sure of why this is done :confused:, document shows that CUPS uses the usb in raw mode, If anybody have any ideas can add details). so before start to configure let us configure to load the usblp module

    > gksu gedit /etc/modprobe.d/blacklist-cups-usblp.confcomment the line prefixing # so that it look like #blacklist usblp, save it and exit. Restart the system so that we will have the usblp module loaded

7. Add Printer (Assuming Model LBP3200)

    > sudo /usr/sbin/lpadmin -p LBP3200 -m CNCUPSLBP3200CAPTK.ppd -v ccp://localhost:59787 -Eyou need to change the printer model and the .ppd files respectively to your printer models

8. Configure Capt Admin demon to route printing to correct usb port

    > sudo /usr/sbin/ccpdadmin -p LBP3200 -o /dev/usb/lp09. Now configure auto start the capt daemon by udev rules by identifying the USB Vendor parameter (cannon vendor id is 0x04a9)

    > gksudo gedit /etc/udev/rules.d/85-canon-capt.rules```
KERNEL=="lp*", SUBSYSTEMS=="usb", ACTION=="add", SYSFS{idVendor}=="04a9", RUN+="/bin/bash /etc/init.d/ccpd start"
KERNEL=="lp*", SUBSYSTEMS=="usb", ACTION=="remove", RUN+="/bin/bash /etc/init.d/ccpd stop"
```Add the above two lines 1st line for starting the service and the second line is to stop the service, this happens automatically when you switch on/off your printer

10. Change the start up script
    > gksu gedit /etc/init.d/ccpdDelete all the existing content and replace it with the below code

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

```Ok, now we are done with the setup lets restart the system and do the finish up step

Finish-up (Power ON the printer before testing this)

1. check if the usb port are properly installed

    > sudo ls /dev/usbyou should see the lp0 in the list


2. Switch on the printer and then type the command below to see the CAPT Admin daemon is running

    > sudo /etc/init.d/ccpd statusThe command should list some thing like this "Canon Printer Daemon for CUPS: ccpd: 1135 1131", there should be two process running (the number will differ)

3. Disabling the auto assigned printer

go to > settings->Printer select the auto selected printer (in my case its LBP3200-2) and change the status to "OFF"

OK that's it you can restart your system one more time if needed and start printing

Good Luck :P

---

### Post by mksundaram on 2011-11-06
Thanks for quick reply:-)
As you mentioned I did as it is :-
1) downloaded the file
2) Extracted the downloaded file; which created this file Linux_CAPT_PrinterDriver_V230_uk_EN (in download dir.)
3)  Downloaded the file which opens with Ubuntu Software center; But after  installing it was showing RE-Install instead of remove and with  installed tick mark. ( I thought some error while installing so RE-  Installed it for the second time but the end result was again the same  RE-Install instead of remove and with installed tick mark. . I let go  and went with next step.
4)  sduo dpkg -i gs-esp_9.01~dfsg~svn12047-0ubuntu1_all.deb  			 		
result was :-
shree@shree-desktop:~$ sudo dpkg -i gs-esp_9.01~dfsg~svn12047-0ubuntu1_all.deb
[sudo] password for shree: 
dpkg: error processing gs-esp_9.01~dfsg~svn12047-0ubuntu1_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 gs-esp_9.01~dfsg~svn12047-0ubuntu1_all.deb
shree@shree-desktop:~$ 

Now what do i do ?


> **rajamohan said:**
> OK now ubuntu 11.10 is out so I thought of updating this thread for the latest version and most recent driver. This time I am going to details the installation of the driver from the existing build direct from the Canon linux driver, below are the steps :)

1. Download the driver from the link [http://support-au.canon.com.au/contents/AU/EN/0900772408.html](http://support-au.canon.com.au/contents/AU/EN/0900772408.html)
2. unzip the downloaded driver assuming you had downloaded to the default folder (Downloads)

    3. This will create a folder "Linux_CAPT_PrinterDriver_V230_uk_EN" in the current directory. You will have four folders inside this, of which we are concerned about two folder i.e "32-bit_Driver" and "64-bit_Driver"

4. Ubuntu 11.10 have a missing package gs-esp so we need to fix that download the .deb package from the link and install it [http://launchpadlibrarian.net/62641639/gs-esp_9.01%7Edfsg%7Esvn12047-0ubuntu1_all.deb](http://launchpadlibrarian.net/62641639/gs-esp_9.01%7Edfsg%7Esvn12047-0ubuntu1_all.deb)

    For 32 Bit System

5. change to folder "32-bit_Driver"

    For 64 Bit System

The driver file contain only contain RPM files so we need to convert it to .deb files, for this we will install a alien package which is a tool to convert RPM to DEB

    Now we need to convert the rpm files (assuming we are in Downloads Folder)

    5. now we have the .deb files we can install the driver

    Let start prepare to start configuring the printer.

6. Ubuntu 11.10 had blacklisted usblp modules (I am not sure of why this is done :confused:, document shows that CUPS uses the usb in raw mode, If anybody have any ideas can add details). so before start to configure let us configure to load the usblp module

    comment the line prefixing # so that it look like #blacklist usblp, save it and exit. Restart the system so that we will have the usblp module loaded

7. Add Printer (Assuming Model LBP3200)

    you need to change the printer model and the .ppd files respectively to your printer models

8. Configure Capt Admin demon to route printing to correct usb port

    9. Now configure auto start the capt daemon by udev rules by identifying the USB Vendor parameter (cannon vendor id is 0x04a9)

    ```
KERNEL=="lp*", SUBSYSTEMS=="usb", ACTION=="add", SYSFS{idVendor}=="04a9", RUN+="/bin/bash /etc/init.d/ccpd start"
KERNEL=="lp*", SUBSYSTEMS=="usb", ACTION=="remove", RUN+="/bin/bash /etc/init.d/ccpd stop"
```Add the above two lines 1st line for starting the service and the second line is to stop the service, this happens automatically when you switch on/off your printer

10. Change the start up script
    Delete all the existing content and replace it with the below code

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

```Ok, now we are done with the setup lets restart the system and do the finish up step

Finish-up

1. check if the usb port are properly installed

    you should see the lp0 in the list


2. Switch on the printer and then type the command below to see the CAPT Admin daemon is running

    The command should list some thing like this "Canon Printer Daemon for CUPS: ccpd: 1135 1131", there should be two process running (the number will differ)

3. Disabling the auto assigned printer

go to  select the auto selected printer (in my case its LBP3200-2) and change the status to "OFF"

OK that's it you can restart your system one more time if needed and start printing

Good Luck :P

---

### Post by HL67 on 2012-01-03
Hi,

I tried to follow the procedure close, but in stage 7 I get:

lpadmin: Bad device-uri scheme "ccp"

In GUI, Printer properties I have device URI: file:///dev/null

So, no luck in printing yet...

Maybe previous attempts have trashed my system somehow. Can you give me some tips how to get device-uri scheme ccp registered?

Thanks,

--Hannu

---

### Post by librechick on 2012-01-03
> **HL67 said:**
> Hi,

I tried to follow the procedure close, but in stage 7 I get:

lpadmin: Bad device-uri scheme "ccp"

In GUI, Printer properties I have device URI: file:///dev/null

So, no luck in printing yet...

Maybe previous attempts have trashed my system somehow. Can you give me some tips how to get device-uri scheme ccp registered?

Thanks,

--Hannu

What I usually do in these situations is test from a live CD. This way you don't trash your system. 

Although I actually avoid most of these issues by not going with hardware dependent on proprietary drivers ([http://www.thinkpenguin.com/](http://www.thinkpenguin.com/) or check out HP's printer list- they identify which printers require non-free firmware / or non-free plug-in) and get hardware that has mainline kernel/and or project support.

---

### Post by HL67 on 2012-01-03
OK, thats a wise strategy. But im not there with this device. LBP6000, to be exact. It should work... That was so close... :)

edit: Just got over this one:

In phase 5 / amd64 I did:

cd Linux_CAPT_PrinterDriver_V230_uk_EN/62-bit_Driver/RPM
    sudo alien *.rpm  **--scripts**

Thanks to this thread at askubuntu.com:

[http://askubuntu.com/questions/79906/installing-lbp-2900-printer-libs-folders-wrong](http://askubuntu.com/questions/79906/installing-lbp-2900-printer-libs-folders-wrong)

Still I cant print, but I doubt whether it is CAPT problem anymore... Every print job turns to "failed" at printer control panel.

edit2: Got over that one, too. 
I did open a window to what's happening at print time:
$ tail - f /var/log/syslog
I learned that Novell AppArmor was blocking much of cups printing. So, I removed AppArmor from my system with Ubuntu Software Center.
Now the print jobs are handled fine, although printer still outputs nothing. In syslog I see that mapping printer usb device to cups device doesnt succeed, somehow... Hmm...

edit3: Further progress and final dead end
I allowed blacklisting of usblp module (undo phase 6). Got better output in syslog: now the interface is registered correctly, or no failures in log, at least.

Still: Ubuntu/cups printing is fine, print job gets completed in reasonable time, but printer outputs nothing. Tried to connect printer to Win7 32-bit, works OK.

I tried to compile 64-bit driver v. 2.40 from source, with no luck. "common" part compiled OK, "capt" part did not (there was "command not found" error after quite a lot of makefiles gone through). 

I haven't time to be in stuck with this anymore. Im doing some arrangements: giving LBP6000 for my wife (she is using Windows 7 64-bit), and using myself HP Officejet 6500 with Linux 64-bit.

---

### Post by prkos on 2012-03-26
I used the above steps from rajamohan with the difference - driver v2.40 and instead of: 
```
sudo alien *.rpm 
```

I used 
```

sudo alien *.rpm --scripts
```

Everything went ok except the printer doesn't print. I get the printing messages but the Job State says Held. 

When I go to the Print dialogue I can see LBP3250 and also LBP3250-2 (which is disabled), for LBP3250 Location is empty (for LBP3250-2 it's the name of my comp), and under Status it says:

/usr/lib/cups/filter/pstocapt3 failed

If I undo step6 (allow blacklisting) the tests fail:
```
sudo ls /dev/usb
```
doesn't show lp0 
and 
```
sudo /etc/init.d/ccpd status
```
doesn't show any process numbers 

The message Printing "some document name" pops up every so often at the bottom of the screen, but nothing happens on the printer. 

Help!

---

### Post by prkos on 2012-03-26
I also tried the script from [http://howandyou.com/how-to-install-canon-lbp-printers-in-ubuntu/](http://howandyou.com/how-to-install-canon-lbp-printers-in-ubuntu/)

and during the install it complained about a dependency: 
libc6-i386 (>= 2.3.2)

so I installed it, closed the Synaptic, started the script again, rebooted but still it won't print. 
Also when I test:
```
sudo /etc/init.d/ccpd status
```
I only get one number (process): 

Canon Printer Daemon for CUPS: ccpd: 642

---

### Post by tora201 on 2012-04-16
I was having nightmares with my LBP6200 in 12.04 64 bit. Anyway, out of all the guides this one with a few extra tweaks (taken from others) worked for me. I assume its the same for the LBP3200 and most other ones too:

1) get the drivers from Canon (Latest are 2.4) and extract. Go to the rpms and alien them in a terminal: sudo alien *.rpm --scripts

2) Install the DEBs normally.

3) copy everything (just to be sure) from: /usr/lib/cups/  to usr/lib64/cups  (create /lib64/cups if doesn't exist)    <---needed because the driver doesn't put all the files we need into lib64! (naughty, Canon)

4) terminal: lsmod | grep usblp

if nothing add: 
ls -l /var/ccpd
sudo mkdir /var/ccpd
sudo mkfifo /var/ccpd/fifo0
sudo chown -R lp:lp /var/ccpd


5) Make better ccpd (See Step 6 in first post of this thread)

6) install printer @ terminal(replace xxxx with your printer model. Mine is 6200)

/usr/sbin/lpadmin -p LBPxxxx -m CNCUPSLBPxxxxCAPTK.ppd -v ccp:/var/ccpd/fifo0 -E

7)/usr/sbin/ccpdadmin -p LBPxxxx -o /dev/usb/lp0

8 ) restart CUPS: sudo service cups restart

9) unplug printer. Re-plug in to USB: Let Ubuntu install driver. Disable it (Right click it, and disable in "printing GUI) Uncheck "Make default"

10) Delete the original LBP we manually installed (Step 6)from within the GUI

11) in the GUI  manually add new printer -> Choose the CAPT one! (Very important)and correct PPD. Make it default. Go to properties and make sure it is: ccp:/var/ccpd/fifo0        

12) re-start CUPS: sudo service cups restart

13) unplug printer. Re-plug it in

14) Start ccpd: sudo /etc/init.d/ccpd start

15) Print a test page.

16) Good luck!! (You'll bloody need it)

Note 1) have tried many ways to automate ccpd on boot, but to no avail. Any ideas that actually work? If not, just do what I do. Boot, unplug printer. re-plug it in (turn on first!) Start ccpd (Step 14) And wait for about 30 secs. THEN print. 

Note 2) The above worked for me. Please feel free to fix my mistakes/order/whatever. If there are shortcuts, please also comment.

---

### Post by Sivella on 2012-04-18
Hello tora201

> 3) copy everything (just to be sure) from: /user/lib/cups/  to  user/lib64/cups      <---needed because the driver doesn't put all  the files we need into lib64! (naughty, Canon)

Are you sure that it is /user/lib/cups and /user/lib64/cups ?
Probably : /usr/lib/cups and /usr/lib64/cups
As far as I know, you must create /usr/lib64/ before copying.

Regards

---

### Post by tora201 on 2012-04-23
Lost patience with 64 bit version of CAPT and went 32 bit.

I know mine is a 6200, but wondering if anybody has a similar problem. Immediately more of a success for 32 bit following instructions from the Wiki. It now works (after manually running ccpd daemon) The problem is it prints just one job. After that, nothing; nada; naught....

If I want to print again, I have to re-boot, and then manually run the ccpd daemon.

Thoughts? Somebody must have some idea?

Cheers.

---

### Post by tonidito on 2012-10-10
Hi, some days ago I decided to upgrade my Ubuntu 10.04 to the newer Ubuntu 12.04. Everything went very well, and after some configuration I felt satisfied. Only a thing created some head scratching: my Canon printer LBP3010 could not print!
After some unsuccessfully attempts to make the driver functioning I decided to make some researches in Google. I tried all possible drivers, deb packages and following strictly all posts that I fount in the Internet, but... nothing, my printer seems to be dead!
My last chance was to recompile from source. First with unsuccessful results, due to many error that occurred during the compilation procedure. Again, after some head scratching and a few sleepless nights analyzing the source code, I get the right solution and now I have my LBP3010 fully functioning.

Note that the following procedure is valid for a 64 bit machine.

uname -a gives
Linux toni-laptop 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

In the following I will show the procedure that I followed in order to get the printer working.
First I downloaded the last driver package I found at the Canon web page:

Linux_CAPT_PrinterDriver_V240_uk_EN.tar.gz.

Now the procedure to compile.

First step
1) extract the tar.gz package to a folder of Your choice;
2) cd Linux_CAPT_PrinterDriver_V240_uk_EN/Src/
3) untar cndrvcups-capt-2.40-1.tar.gz  and cndrvcups-common-2.40-1.tar.gz
4) cd cndrvcups-common-2.40/
5) gedit debian/control and change "i386" with "amd64" al line 9, save and close file
6) dpkg-buildpackage.

At the end of operation 6) You will find cndrvcups-common_2.40-1_amd64.deb package in Src directory.

7) install it (required for the next compilation steps) with the common 
    sudo dpkg -i cndrvcups-common_2.40-1_amd64.deb

Second step
1) cd cndrvcups-capt-2.40/
2) gedit debian/control and change "i386" with "amd64" al line 9, save and close file
3) gedit debian/rules and uncomment line 172 which will results, then, in 
    #    dh_shlibdeps
    Save and close
4) gedit statusui/src/ppapdata.c and add the header (this is to define variable ppd_size_t)
    #include <cups/ppd.h>
save and close file.
5) gedit cngplp/configure.in and add "AC_CONFIG_MACRO_DIR([m4])" at line 9, save and close
6) gedit cngplp/Makefile.am and add "ACLOCAL_AMFLAGS=-I m4" at line 5, save and close
7) run the following commands in the cngplp directory:
libtoolize
    aclocal
    automake
8) cd .. 
9) dpkg-buildpackage

At the end of operation 9) You will find cndrvcups-capt_2.40-1_amd64.deb package in Src directory.

10) install it with 
    sudo dpkg -i cndrvcups-capt_2.40-1_amd64.deb

End of procedure.
From this point You should follow the printer configuration steps as stated in the previous posts.:p

I hope this will help the Ubuntu Community.
Kind regards

---

