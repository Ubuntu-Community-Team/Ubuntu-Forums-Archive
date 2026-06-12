---
title: "Canon LBP3050 printer"
date: 2012-06-05
forum: Hardware
---

### Post by BigBaka on 2012-06-05
Hi,

I've been following this guide to install a Canon LBP3050 printer
[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)
But while following these steps for installation in 12.04 I came across the following error.
> 
root@CF1:/etc/init.d# /usr/sbin/lpadmin -p LBP3050 -m CNCUPSLBP3050CAPTK.ppd -v ccp://localhost:59787 –E
lpadmin: Unknown argument "–E".


Totally stuck! If someone could advise I'd be most appreciative.

Ta,
BB

---

### Post by Sivella on 2012-06-06
Hello,

First of all, tell us if you are running 12.04  **32 or 64bits**.
The procedure is quite different.
Thanks.

---

### Post by BigBaka on 2012-06-06
Ummm, that would be 32

---

### Post by Sivella on 2012-06-07
OK, 32bits is the simplest because you can use the 32bits drivers provided by Canon.

I assume you have installed *cndrvcups-common_2.40-1_i386.deb* first, and  then *cndrvcups-capt_2.40-1_i386.deb* without any error messages, and you have rebooted the PC since.

In   System Settings --> Printing : Remove all the LBP printers.

Here is the procedure:

1) Edit file : /etc/modprobe.d/blacklist-cups-usblp.conf
> gksudo gedit /etc/modprobe.d/blacklist-cups-usblp.conf[INDENT] Comment (#) the line : blacklist usblp.
[/INDENT]Here is the file :
> # cups talks to the raw USB devices, so we need to blacklist usblp to avoid
# grabbing them
#blacklist usblp                      2) Create the following directories/file if they are missing:
> sudo mkdir /var/ccpd
sudo mkfifo /var/ccpd/fifo0
sudo mkdir /var/captmon                      3)  Register the printer :
> sudo /usr/sbin/lpadmin -p LBP3050 -m CNCUPSLBP3050CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E                      4) Register the printer with ccpd daemon :
> sudo /usr/sbin/ccpdadmin -p LBP3050 -o /dev/usb/lp0                      5)  Start ccpd daemon :
> sudo /etc/init.d/ccpd start                      Test install :
> captstatusui -P LBP3050                      will open the Statusmonitor window. If the message "Ready to print" is displayed --> all is OK.
Try to print something.

In   System Settings --> Printing :   set your LBP3050 as default (right click on LBP3050 icon)
Probably on next boot, a "new" LBP3050-2 will appear. Don't worry about that and ignore it (the default is LBP-3050).


If every things are OK, you can now follow this procedure to manage automatically ccpd deamon.

1) Create an udev rule in order to detect when the printer appear/disappear on the USB bus.[INDENT]Create the file:
> gksudo gedit /etc/udev/rules.d/85-canon-capt.rules                      Put inside :
> KERNEL=="lp*", SUBSYSTEM=="usb", ACTION=="add", ATTRS{idVendor}=="04a9", RUN+="/etc/init.d/ccpd start"
KERNEL=="lp*", SUBSYSTEM=="usb", ACTION=="remove", RUN+="/etc/init.d/ccpd stop"                      Save this file and close the Editor.

[/INDENT]2) Modify the file    */lib/udev/rules.d/70-printers.rules* :[INDENT]> gksudo gedit /lib/udev/rules.d/70-printers.rules                      Put   **#**   at the beginning of line n°4. The file looks like that:
> # Low-level USB device add trigger
ACTION=="add", SUBSYSTEM=="usb", ATTR{bInterfaceClass}=="07",  ATTR{bInterfaceSubClass}=="01", TAG+="udev-configure-printer",  RUN+="udev-configure-printer add %p"
# usblp device add trigger (needed when usblp is already loaded)
#ACTION=="add", KERNEL=="lp*", TAG+="udev-configure-printer", RUN+="udev-configure-printer add %p"
# Low-level USB device remove trigger
ACTION=="remove", SUBSYSTEM=="usb", ENV{ID_USB_INTERFACES}=="*:0701*:*", RUN+="udev-configure-printer remove %p"                      **_Take care it is a system file. It could me modified in the future by  an update.  So keep in mind, if the printer stops working, have a look to  this file... _**

[/INDENT]3) Create an Upstart Job :[INDENT]> gksudo gedit /etc/init/ccpd-restart.conf                      Put inside:
> # ccpd-restart - if printer is ON before PC.
description    "restart daemon ccpd for Canon printer LBP-serie"

start on started cups
stop on runlevel [016]

script[INDENT]if [ -e /dev/usb/lp* ]; then[INDENT]/etc/init.d/ccpd stop
sleep 3
/etc/init.d/ccpd start
[/INDENT]fi
[/INDENT]end script                                 Save and close Editor.
[/INDENT]That all. :wink: 
Normally, you don't have to take care any more about your printer. It  can be switched on/off/on/off... while PC is running, it can be switched  on before starting PC, it will be always "ready to print".


Nota :
If you are enough comfortable with French language, you can find accurate explanations in "doc-ubuntu".
I'm one of the "main" contributor (named murex) for Canon LBP.
[http://doc.ubuntu-fr.org/tutoriel/in...lote_canon_lbp]("http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp")

Good luck

---

### Post by petercool on 2013-04-15
> **Sivella said:**
> Hello,

First of all, tell us if you are running 12.04  **32 or 64bits**.
The procedure is quite different.
Thanks.

How about 64bits?
I've been searching the solution to 64bits for many  months......sigh!
Thanks a million.....

---

### Post by schragge on 2013-04-15
The French tutorial linked above recommends installing *ia32-libs* from *oneiric* (Ubuntu 11.10). However, recent Ubuntu releases support the [multiarch specification](http://wiki.debian.org/Multiarch), so 32-bit packages should be installable on a 64-bit system as is. At least, give it a try.

---

### Post by pdc on 2013-04-15
Hi to Petercool;

the administrators of the forum suggest you start a new thread; when you have a new problem; that often helps bring your problem to the attention of others; and keeps you away from much older information; 

however in this thread Sivella posted a link to an excellent tutorial;

..............sigh...................have a read at it; ......................sigh..............................

[http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

the steps are:
1)install 2.5 CAPT driver from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html) (more detail can be supplied if needed)
1.1) for 64bit install various needed accessories
2.1) install command
2.2) installation validation
3) automate detection of printer

in general with the LBP series and ubuntu: there are 2 choices:

1) 32bit .........a simple install
2) 64bit.......more work ......................sigh........................................... :D

---

### Post by petercool on 2013-04-15
> **pdc said:**
> Hi to Petercool;

the administrators of the forum suggest you start a new thread; when you have a new problem; that often helps bring your problem to the attention of others; and keeps you away from much older information; 

however in this thread Sivella posted a link to an excellent tutorial;

..............sigh...................have a read at it; ......................sigh..............................

[http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

the steps are:
1)install 2.5 CAPT driver from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html) (more detail can be supplied if needed)
1.1) for 64bit install various needed accessories
2.1) install command
2.2) installation validation
3) automate detection of printer

in general with the LBP series and ubuntu: there are 2 choices:

1) 32bit .........a simple install
2) 64bit.......more work ......................sigh........................................... :D

Thanks for your professional advice.
p.s. :popcorn: If I still can't solve the problem in a few days,I'll do it soon.Thank you! ;)

---

### Post by petercool on 2013-04-15
> **schragge said:**
> The French tutorial linked above recommends installing *ia32-libs* from *oneiric* (Ubuntu 11.10). However, recent Ubuntu releases support the [multiarch specification](http://wiki.debian.org/Multiarch), so 32-bit packages should be installable on a 64-bit system as is. At least, give it a try.

Yeah,I had read that tutorial before,but still didn't undertand completely!Even though i used google translation!And I found that I already had installed ia32-libs multiarch too...It still didn't print anything yet!
Anyway,thx for your reply.:popcorn:

---

### Post by schragge on 2013-04-16
Just installing *ia32-libs* on releases starting from *precise* (Ubuntu 12.04) won't help as it is a dummy package now. You should either install ia32-libs from *oneiric* as recommended in the tutorial or install 32-bit libraries CAPT driver depends on by hand or rebuild the driver from source.

---

### Post by petercool on 2013-04-16
> **schragge said:**
> Just installing *ia32-libs* on releases starting from *precise* (Ubuntu 12.04) won't help as it is a dummy package now. You should either install ia32-libs from *oneiric* as recommended in the tutorial or install 32-bit libraries CAPT driver depends on by hand or rebuild the driver from source.

Thanks,I'll try....\\:D/

---

