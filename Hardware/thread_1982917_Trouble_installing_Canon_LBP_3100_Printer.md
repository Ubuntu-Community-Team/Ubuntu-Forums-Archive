---
title: "Trouble installing Canon LBP 3100 Printer"
date: 2012-05-19
forum: Hardware
---

### Post by theunsheydenrych on 2012-05-19
HI , can someone please help.
I am trying to get my Canon LBP 3100 Printer working from Ubuntu12.04.

I downloaded the drivers from [http://gdlp01.c-wss.com/gds/4/0900007724/12/Linux_CAPT_PrinterDriver_V240_uk_EN.tar.gz](http://gdlp01.c-wss.com/gds/4/0900007724/12/Linux_CAPT_PrinterDriver_V240_uk_EN.tar.gz) and installed them.

When connecting the printer via usb it automatically adds a printer with the "Canon LBP3100/LBP3108/LBP3150 CAPT (UK)" selected with a device uri "usb://Canon/LBP3100/LBP3108/LBP3150?serial=0000B1A2R5MJ", when printing a test page it just sits there with the status message "Processing - Sending data to printer."

I also tried to add the printer according to a few other sites.
By configuring it via.through cups with a device uri "ccp:/var/ccpd/fifo0", when printing a test page from here the status is just "Processing"

When using the ```
captstatusui -P LBP3100 command
```, its tels me that the printer is not on (though its is), or the cable is not connected(though its is), when switching the printer on and off, it states "waiting" then it closes.

I dont know what else to do? 
Any suggestions?

---

### Post by Sivella on 2012-05-21
Hello,

First of all, are you running 32 or 64bits version of 12.04 ?

The automatic detection/add printers is not relevant for Canon printer using CAPT drivers. You must install it manually, but some steps in the procedure are not the same depending 32 or 64bits.

---

### Post by theunsheydenrych on 2012-05-21
Thank you for the reply.

Its 32bit Ubuntu 12.04 version, and i installed the 32bit .deb packages for the driver i downloaded from the link mentioned above.
I would be very glad if i can get help, thanks.

---

### Post by Sivella on 2012-05-21
Ok, 32bits is the simplest  ;-)

Firts, in :   System Settings --> Printing
Remove any printer(s).

I assume you have installed cndrvcups-common_2.40-1_i386.deb first, and then cndrvcups-capt_2.40-1_i386.deb without any error messages.

1) Create the following directories/file if they are missing:
> sudo mkdir /var/ccpd
sudo mkfifo /var/ccpd/fifo0
sudo mkdir /var/captmon                      2)  Register the printer:
> sudo /usr/sbin/lpadmin -p LBP3100 -m CNCUPSLBP3150CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E                      CNCUPSLBP3150CAPTK.ppd is not a mistake...

3) Register the printer with ccpd daemon:
> sudo /usr/sbin/ccpdadmin -p LBP3100 -o /dev/usb/lp0                      4)  Start ccpd daemon:
> sudo /etc/init.d/ccpd start                      Test install:
> captstatusui -P LBP3100                      will open the Statusmonitor window. If the message "Ready to print" is displayed --> all is OK.
Try to print something.

In   System Settings --> Printing   set your LBP3100 as default (right click on LBP3100 icon)
Probably on next boot, a "new" LBP3100-2 will appear. Don't worry about that and ignore it (the default is LBP-3100).  

If it works well, I will explain you how to  manage automatically ccpd daemon.

Good luck.

---

### Post by theunsheydenrych on 2012-05-22
Thank you Sivella, for your reply and help.
The advice works for me!  :p
 
When rebooting the laptop, the default printer is there and no new printer is created.
I have to start the ccpd deamon after every reboot before the printer can print, i presume the rest of the instructions  is regarding the start of this deamon on startup? 

Thanks, again

---

### Post by Sivella on 2012-05-23
OK, thanks for typo errors, I have corrected my post.

So, now here is how to manage automatically ccpd deamon.

1) Create an udev rule in order to detect when the printer appear/disappear on the USB bus.[INDENT]Create the file:
> gksudo gedit /etc/udev/rules.d/85-canon-capt.rulesPut inside :
> KERNEL=="lp*", SUBSYSTEM=="usb", ACTION=="add", ATTRS{idVendor}=="04a9", RUN+="/etc/init.d/ccpd start"
KERNEL=="lp*", SUBSYSTEM=="usb", ACTION=="remove", RUN+="/etc/init.d/ccpd stop"Save this file and close the Editor.

[/INDENT]2) Modify the file    */lib/udev/rules.d/70-printers.rules* :[INDENT]> gksudo gedit /lib/udev/rules.d/70-printers.rulesPut   **#**   at the beginning of line n°4. The file looks like that:
> # Low-level USB device add trigger
ACTION=="add", SUBSYSTEM=="usb", ATTR{bInterfaceClass}=="07", ATTR{bInterfaceSubClass}=="01", TAG+="udev-configure-printer", RUN+="udev-configure-printer add %p"
# usblp device add trigger (needed when usblp is already loaded)
#ACTION=="add", KERNEL=="lp*", TAG+="udev-configure-printer", RUN+="udev-configure-printer add %p"
# Low-level USB device remove trigger
ACTION=="remove", SUBSYSTEM=="usb", ENV{ID_USB_INTERFACES}=="*:0701*:*", RUN+="udev-configure-printer remove %p"_Take care it is a system file. It could me modified in the future by an update. So keep in mind, if "auto ccpd" stops working, have a look to this file... _

[/INDENT]3) Create an Upstart Job :[INDENT]Create the file:
> gksudo gedit /etc/init/ccpd-restart.confPut inside:
> # ccpd-restart - if printer is ON before PC.
description    "restart daemon ccpd for Canon printer LBP-serie"

start on started cups
stop on runlevel [016]

script[INDENT]if [ -e /dev/usb/lp* ]; then[INDENT]/etc/init.d/ccpd stop
sleep 3
/etc/init.d/ccpd start
[/INDENT]fi
[/INDENT]end script[/INDENT][INDENT]Save and close Editor.
[/INDENT]That all. ;) 
Normally, you don't have to take care any more about your printer. It can be switched on/off/on/off... while PC is running, it can be switched on before starting PC, it will be always "ready to print".


Nota :
If you are enough comfortable with French language, you can find accurate explanations in "doc-ubuntu".
I'm one of the "main" contributor (named murex) for Canon LBP.
[http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

Good luck

---

### Post by theunsheydenrych on 2012-05-23
Thanks again Sivella.
This instructions works for me!
Thanks again for the great way the instructions was given, it was really easy and without any trouble to install the Canon LBP3100 laser printer.

Just a little back ground, about why i got the Canon printer.
A lady friend of my parents in law (78 years young:)) wanted to type here recipes on computer (WinXP at the time) because her recipe books is fallen apart and she still had a old dot matrix printer, so i suggested the Canon LBP3100 because it was +-$95 and the laser printer cartridge for domestic usage will keep a long time before it needs replacing.  But i did check if there is a linux driver available. Now two years later i suggested she move to ubuntu (more secure and stable) because she was very weary and scared of all the viruses etc...

So now she is sorted, she can internet, email, skype and print.

Thanks again 
:popcorn:

---

### Post by Sivella on 2012-05-24
It was a pleasure, and I'm very happy for this young lady ;) and I wish a long and happy "Ubuntu life".
Hopefully, she is running Ubuntu 32bits, and Canon provide DEB package-drivers ONLY for 32bits.
The installation procedure is a more complicated with 64bits.

Don't forgot the *70-printers.rules* file if suddenly the printer stop working.

All the best.

---

### Post by Sivella on 2012-06-06
Hello theunsheydenrych,

Due to a new cups update, it seems that usblp module is now blacklisted (like it was with 11.10).
So the printer is not mounted in /dev/usb.

The solution is to cancel this blacklist.

Edit this file : /etc/modprobe.d/blacklist-cups-usblp.conf

Comment (#) the line : blacklist usblp
Here is my file :
> # cups talks to the raw USB devices, so we need to blacklist usblp to avoid
# grabbing them
#blacklist usblp

---

### Post by maxim40 on 2012-06-12
Hi Sivella,

Could you please give me the instructions for 64-bit driver installation (Canon lbp 3000) in ubuntu 12.04?

Thanks in advance.

> **Sivella said:**
> Hello theunsheydenrych,

Due to a new cups update, it seems that usblp module is now blacklisted (like it was with 11.10).
So the printer is not mounted in /dev/usb.

The solution is to cancel this blacklist.

Edit this file : /etc/modprobe.d/blacklist-cups-usblp.conf

Comment (#) the line : blacklist usblp
Here is my file :

---

### Post by Sivella on 2012-06-12
Hello maxim40

Here is how to run your LBP3000 in Ubuntu 12.04-64bits.

For a LBP3000, the simplest way is to download drivers from the PPA mickael-gruz.
The 64bits Maverick version works well with 12.04.

1)  Download and install transitional package "gs-esp" :[INDENT][http://packages.ubuntu.com/lucid/gs-esp](http://packages.ubuntu.com/lucid/gs-esp)
[/INDENT]2)  Download and install from the PPA depot the 2 packages :[INDENT][https://launchpad.net/~michael-gruz/+archive/test/+build/2216444/+files/cndrvcups-common_2.20-1ubuntu4_amd64.deb]("https://launchpad.net/%7Emichael-gruz/+archive/test/+build/2216444/+files/cndrvcups-common_2.20-1ubuntu4_amd64.deb")

[https://launchpad.net/~michael-gruz/+archive/test/+build/2216478/+files/cndrvcups-capt_2.20-1ubuntu3_amd64.deb]("https://launchpad.net/%7Emichael-gruz/+archive/test/+build/2216478/+files/cndrvcups-capt_2.20-1ubuntu3_amd64.deb")

[B]Install first cndrvcups-common.
[/B][/INDENT]3) Restart cups :[INDENT]> sudo service cups restart[/INDENT]4) Modify the file */etc/modprobe.d/blacklist-cups-usblp.conf  *as indicated in my post #9

5) See my post #5 in : [http://ubuntuforums.org/showthread.php?t=1983091](http://ubuntuforums.org/showthread.php?t=1983091)[INDENT]Starting at point#1 and of course  change LBP6300 with LBP3000

[/INDENT]If you succeed to print,  see my post#6 in this thread for auot-ccpd management.
Good luck  ;)

---

### Post by maxim40 on 2012-06-12
Thank you very much for your help.

I had a problem with ia32-libs.

I have download the file "ia32-libs_20090808ubuntu26_amd64.deb" but when i try to install it the install package button is disabled so i cannot continue. 

Do you know why?



> **Sivella said:**
> Hello maxim40

Here is how to run your LBP3000 in Ubuntu 12.04-64bits.

For a LBP3000, the simplest way is to download drivers from the PPA mickael-gruz.
The 64bits Maverick version works well with 12.04.

1)  Download and install transitional package "gs-esp" :[INDENT][http://packages.ubuntu.com/lucid/gs-esp](http://packages.ubuntu.com/lucid/gs-esp)
[/INDENT]2)  Download and install from the PPA depot the 2 packages :[INDENT][https://launchpad.net/~michael-gruz/+archive/test/+build/2216444/+files/cndrvcups-common_2.20-1ubuntu4_amd64.deb]("https://launchpad.net/%7Emichael-gruz/+archive/test/+build/2216444/+files/cndrvcups-common_2.20-1ubuntu4_amd64.deb")

[https://launchpad.net/~michael-gruz/+archive/test/+build/2216478/+files/cndrvcups-capt_2.20-1ubuntu3_amd64.deb]("https://launchpad.net/%7Emichael-gruz/+archive/test/+build/2216478/+files/cndrvcups-capt_2.20-1ubuntu3_amd64.deb")

[B]Install first cndrvcups-common.
[/B][/INDENT]3) Restart cups :[INDENT][/INDENT]4) Modify the file */etc/modprobe.d/blacklist-cups-usblp.conf  *as indicated in my post #9

5) See my post #5 in : [http://ubuntuforums.org/showthread.php?t=1983091](http://ubuntuforums.org/showthread.php?t=1983091)[INDENT]Starting at point#1 and of course  change LBP6300 with LBP3000

[/INDENT]If you succeed to print,  see my post#6 in this thread for auot-ccpd management.
Good luck  ;)

---

### Post by Sivella on 2012-06-13
Try command line in a terminal.

First move in the directory where this package is (with "cd" command), then :
> sudo dpkg -i ia32-libs_20090808ubuntu26_amd64.debMay be it doesn't work in graphic mode because a transitional package *ia32-libs* exists for 12.04 and the application is reluctant to install a downgraded version ?

---

### Post by maxim40 on 2012-06-13
Hi Sivella,

I try it but again i have an error. I think you are right, the problem might be this. How can i install it?

Thank you

root@Core-i5:/home/dionysos/Downloads# sudo dpkg -i ia32-libs_20090808ubuntu26_amd64.deb
dpkg: regarding ia32-libs_20090808ubuntu26_amd64.deb containing ia32-libs, pre-dependency problem:
 ia32-libs pre-depends on libc6-i386 (>= 2.9-18 )
dpkg: error processing ia32-libs_20090808ubuntu26_amd64.deb (--install):
 pre-dependency problem - not installing ia32-libs
Errors were encountered while processing:
 ia32-libs_20090808ubuntu26_amd64.deb


> **Sivella said:**
> Try command line in a terminal.

First move in the directory where this package is (with "cd" command), then :
May be it doesn't work in graphic mode because a transitional package *ia32-libs* exists for 12.04 and the application is reluctant to install a downgraded version ?

---

### Post by Sivella on 2012-06-14
Before installing* ia32-libs*, you must install dependencies :
lib32asound2,
lib32ffi6,
lib32bz2-1.0,
lib32gcc1,
lib32stdc++6,
lib32z1,
lib32ncurses5,
lib32ncursesw5,
libc6-i386,
You can use the 12.04 version they work...

Reading you error message, I think *libc6-i386* is missing. Could you check it ?

---

### Post by maxim40 on 2012-06-15
I finally made it, thank you very very much. The only think that i want to mention, for other users also, is that i have to restart printer in order to print.

> **Sivella said:**
> Before installing* ia32-libs*, you must install dependencies :
lib32asound2,
lib32ffi6,
lib32bz2-1.0,
lib32gcc1,
lib32stdc++6,
lib32z1,
lib32ncurses5,
lib32ncursesw5,
libc6-i386,
You can use the 12.04 version they work...

Reading you error message, I think *libc6-i386* is missing. Could you check it ?

---

### Post by doctorbiju on 2012-06-26
[FONT=Verdana][SIZE=2]Thanks Sivella for excellent  installation instructions  for the printer.   My printer is canon LBP 2900, I had substituted this for LBP 3100.  I am very much new to ubuntu, and I had installed ubuntu 12.04. As I am not technically well versed, I copied all the commands to terminal and [/SIZE][/FONT][FONT=Verdana]everything worked fine.[/FONT][FONT=Verdana][SIZE=2] When I had hit the road block this instruction to  cancel blacklist usblp really helped.[/SIZE][/FONT]

---

### Post by pdc on 2012-07-02
thanks very much for this excellent guide; (post #4)

I have my LBP3100B running well now on Mint 13 (32bit):

c'est tres bien! merci a vous

the directory /var/fif0 was not created with the initial .deb drivers so I was able to do this with the commands you advised;

---

### Post by tonidito on 2012-11-12
Hi,
please follow instructions at the following web page:

[http://ubuntuforums.org/showthread.p...5#post12350075]("http://ubuntuforums.org/showthread.php?p=12350075#post12350075")
(#12)

and You will solve the problem with Canon CAPT printer drivers!

tonidito:razz:

---

### Post by YJie on 2012-12-14
> **Sivella said:**
> Ok, 32bits is the simplest  ;-)

Firts, in :   System Settings --> Printing
Remove any printer(s).

I assume you have installed cndrvcups-common_2.40-1_i386.deb first, and then cndrvcups-capt_2.40-1_i386.deb without any error messages.

1) Create the following directories/file if they are missing:
2)  Register the printer:
CNCUPSLBP3150CAPTK.ppd is not a mistake...

3) Register the printer with ccpd daemon:
4)  Start ccpd daemon:
Test install:
will open the Statusmonitor window. If the message "Ready to print" is displayed --> all is OK.
Try to print something.

In   System Settings --> Printing   set your LBP3100 as default (right click on LBP3100 icon)
Probably on next boot, a "new" LBP3100-2 will appear. Don't worry about that and ignore it (the default is LBP-3100).  

If it works well, I will explain you how to  manage automatically ccpd daemon.

Good luck.



Hi, I am using canon LBP6000. I have no problem installing ndrvcups-common_2.40-1_i386.deb first, and then cndrvcups-capt_2.40-1_i386.deb

I followed every step and changed this line 
> sudo /usr/sbin/lpadmin -p LBP6000 -m CNCUPSLBP6018CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E

Everything went fine until I typed this in the terminal
> captstatusui -P LBP6000
It showed
> *** captstatusui Socket Error ***

I don't know what did I do wrong. Could you please tell me my mistakes?

---

### Post by acronim on 2013-01-06
@[Sivella]("http://ubuntuforums.org/member.php?u=1617603")
All my efforts to install the printer LBP3100B on Ubuntu 12.10 64-bit failed! may you review the way I done?
I got it two ways.
[COLOR=Magenta]FIRST way[/COLOR]: that is describe here:  [http://ubuntuforums.org/showpost.php?p=12415187&postcount=5](http://ubuntuforums.org/showpost.php?p=12415187&postcount=5) -> #5 -> (failed)
[COLOR=Magenta]SECOND way[/COLOR]: the way you respond to #11 in this post that I have done the following: (red lines are the errors that occurred)

1)  Download and install:
```
[http://packages.ubuntu.com/lucid/gs-esp](http://packages.ubuntu.com/lucid/gs-esp)
```[COLOR=Red]
This package wasn't available for 12.10: [http://packages.ubuntu.com/quantal/gs-esp](http://packages.ubuntu.com/quantal/gs-esp) -> ERROR[/COLOR]
[COLOR=Red]So I installesd lucid package on quantal![/COLOR]

2)  Download and install this 2 packages:
```
[https://launchpad.net/~michael-gruz/+archive/test/+build/2216444/+files/cndrvcups-common_2.20-1ubuntu4_amd64.deb]("https://launchpad.net/%7Emichael-gruz/+archive/test/+build/2216444/+files/cndrvcups-common_2.20-1ubuntu4_amd64.deb")
[https://launchpad.net/~michael-gruz/+archive/test/+build/2216478/+files/cndrvcups-capt_2.20-1ubuntu3_amd64.deb]("https://launchpad.net/%7Emichael-gruz/+archive/test/+build/2216478/+files/cndrvcups-capt_2.20-1ubuntu3_amd64.deb")
```3) Restart cups:
```
sudo service cups restart
```4)  Edit this file : /etc/modprobe.d/blacklist-cups-usblp.conf and Comment (#) the line : blacklist usblp
[COLOR=Red] There wasn't this file on /etc direction. So I created it an add these lines whithin:[/COLOR]
```
# cups talks to the raw USB devices, so we need to blacklist usblp to avoid
# grabbing them
#blacklist usblp 
```5) Create the following directories/file if they are missing:
```
 sudo mkdir /var/ccpd
sudo mkfifo /var/ccpd/fifo0
sudo mkdir /var/captmon 
```6) have to install "by hand" the 11.10 ([COLOR=Red]onieric[/COLOR])  ia32-libs package. Install the dependences needed -> quantal 12.10
```
libc6-i386
lib32ncursesw5
lib32asound2
lib32ncurses5
lib32z1
lib32stdc++6
lib32gcc1
lib32bz2-1.0
lib32ffi6
```7) Download and install [http://packages.ubuntu.com/quantal/ia32-libs]("http://packages.ubuntu.com/oneiric/ia32-libs") (for 12.10: quantal)

8) Run the below command
```
echo "ia32-libs hold" | sudo dpkg --set-selections
```9)  Register the printer:
```
sudo /usr/sbin/lpadmin -p LBP3100B -m CNCUPSLBP3150CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
```[COLOR=Red] 3150? -> according this page: [https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)[/COLOR]

10) Register the printer with ccpd daemon:
```
sudo /usr/sbin/ccpdadmin -p LBP3100B -o /dev/usb/lp0 
```[COLOR=Red]During Running this command I got a gnome-keyring error. I  solved it following  [http://askubuntu.com/questions/127848/wine-cant-find-gnome-keyring-pkcs11-so](http://askubuntu.com/questions/127848/wine-cant-find-gnome-keyring-pkcs11-so)[/COLOR]

11)   Start ccpd daemon:
```
sudo /etc/init.d/ccpd start
```12) Test install:
```
captstatusui -P LBP6300
```> **Sivella said:**
> 
will open the Statusmonitor window. If the message &quot;Ready to print&quot; is displayed --&gt; all is OK. Try to print something
the Statusmonitor windowopens but the box is empty. the printer didn't work.

What should I do?

---

### Post by acronim on 2013-01-08
Up;
Please !!!

---

### Post by acronim on 2013-01-10
@[maxim40]("http://ubuntuforums.org/member.php?u=712999")
Could you run your LBP printer on your 64-bit machine?

---

### Post by earshariff on 2013-01-20
hi Sivella i have a cannon 2900 i have followd ur instruction 
By just replacing the ppd file name with my respective file name 
> 
ehab@ehab:~$ sudo mkdir /var/ccpd/fifo0
ehab@ehab:~$ sudo mkdir /var/ccptmon
ehab@ehab:~$ sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
ehab@ehab:~$ sudo /etc/init.d/ccpd start
Starting /usr/sbin/ccpd: .
ehab@ehab:~$ captstatusui -P LPB2900
*** captstatusui Error: No Specified Printer ***
ehab@ehab:~$ captstatusui -p LPB2900
captstatusui --- Status monitor for Canon CAPT Printer.
Usage  :  captstatusui -P printer [-e]
 -e	"Status Monitor is showed only when errors occur".

ehab@ehab:~$ captstatusui -P LPB2900
*** captstatusui Error: No Specified Printer ***
ehab@ehab:~$ captstatusui -P LBP2900





the message says

"NO Specified Printer"

and the text area reads
"Check the <Printer ***> of /etc/ccpd.conf"

help pls thanks in advance

---

### Post by ernstblaauw on 2013-02-09
Hi all,

I also tried to install the drivers on my Linux Minut 12.04 64-bit. I have the LBP7200Cdn printer connected using USB.

What I did:
- Installed the gs-esp transitional package
- Downgraded ia32libs 
- Tried the 2.20 drivers from the earlier mentioned ppa and tried the 2.40 and 2.50 drivers using alien (sudo alien *.deb --scripts).

To install those drivers, I putted them into the 'deb' subdirectory and ran the following script:
```
sudo /usr/sbin/ccpdadmin -x LBP7200C
sudo /etc/init.d/ccpd stop
sudo service cups stop
sudo rm /etc/cups/printers.conf
sudo apt-get --purge remove cndrv*
sudo dpkg -i deb/cndrvcups-common*.deb
sudo dpkg -i deb/cndrvcups-capt*.deb
sudo service cups restart
sleep 5
sudo /usr/sbin/lpadmin -p LBP7200C -m CNCUPSLBP7200CCAPTK.ppd -v ccp://localhost:59787 -E
sudo /usr/sbin/ccpdadmin -p LBP7200C -o /dev/usb/lp0 
sleep 5
sudo /etc/init.d/ccpd start
sleep 5
sudo /etc/init.d/ccpd status
```

I got to the point where the Status Monitor shows info about the printer. However, if I try to print, the Status Monitor sais 'Communication Error'.

Do you guys have an idea what I can do?

---

### Post by pdc on 2013-02-10
hi ernstblaauw; .........everyone would like to see your system working;

sadly, these LBP capt drivers seem to work on 32bit systems; and sometimes it might be worth creating a small partition of a 32bit system: eg Mint is now at Mint 14; and the capt drivers seem fine that way...

---

### Post by ernstblaauw on 2013-02-10
Yes, I know it is difficult at the moment. However, I think there should be a solution to this as a 64-bit rpm package exists and thus I conclude it should be possible on 64-bit Ubuntu and derivatives. Today, I tried to compile the source by hand (v2.50) but still no luck.

At the moment, I use my Windows 7 partition to print :-(.

---

### Post by Billy02 on 2013-03-04
> **Sivella said:**
> Hello maxim40

Here is how to run your LBP3000 in Ubuntu 12.04-64bits.

For a LBP3000, the simplest way is to download drivers from the PPA mickael-gruz.
The 64bits Maverick version works well with 12.04.

1)  Download and install transitional package "gs-esp" :[INDENT][http://packages.ubuntu.com/lucid/gs-esp](http://packages.ubuntu.com/lucid/gs-esp)
[/INDENT]
2)  Download and install from the PPA depot the 2 packages :[INDENT][https://launchpad.net/~michael-gruz/+archive/test/+build/2216444/+files/cndrvcups-common_2.20-1ubuntu4_amd64.deb]("https://launchpad.net/%7Emichael-gruz/+archive/test/+build/2216444/+files/cndrvcups-common_2.20-1ubuntu4_amd64.deb")

[https://launchpad.net/~michael-gruz/+archive/test/+build/2216478/+files/cndrvcups-capt_2.20-1ubuntu3_amd64.deb]("https://launchpad.net/%7Emichael-gruz/+archive/test/+build/2216478/+files/cndrvcups-capt_2.20-1ubuntu3_amd64.deb")

[B]Install first cndrvcups-common.
[/B][/INDENT]
3) Restart cups :4) Modify the file */etc/modprobe.d/blacklist-cups-usblp.conf  *as indicated in my post #9

5) See my post #5 in : [http://ubuntuforums.org/showthread.php?t=1983091](http://ubuntuforums.org/showthread.php?t=1983091)[INDENT]Starting at point#1 and of course  change LBP6300 with LBP3000

[/INDENT]
If you succeed to print,  see my post#6 in this thread for auot-ccpd management.
Good luck  ;)

Hiya Sivella I was wondering if you could help me. I have just freshly installed Ubuntu 12.10 64 bit and am trying to install my Canon LBP 2900i laser printer. I followed your instructions and installed the gs-esp file, but the links in the 2nd instructions have gone down. I was wondering if the installation process has changed?

---

### Post by ernstblaauw on 2013-07-04
I just installed version 2.56 ([http://support-au.canon.com.au/contents/AU/EN/0100459602.html](http://support-au.canon.com.au/contents/AU/EN/0100459602.html)), which contains a 64-bit deb archive! The guy here ([http://askubuntu.com/questions/216933/canon-lbp5050-recognized-but-doesnt-print/304538#304538](http://askubuntu.com/questions/216933/canon-lbp5050-recognized-but-doesnt-print/304538#304538)) succeeded in printing on his LBP7200Cdn, but on my 64-bit Ubuntu Mint 13, I'm not so lucky.

Does anyone here succeed in printing on 64-bit?

---

### Post by pdc on 2013-07-04
the best guide is I think this

[http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp) (translate with google into your favourite language: but BEWARE; google translate adds mysterious spaces in syntax such as ls / usr / share / cups / model / | grep CNCUPS so you need to remove spaces

you can see Sivella talks about adding bits for a 64bit system.......before installing the drivers

can we check: 

1) you installed the common driver (cndrvcups-[COLOR="#0000FF"]common[/COLOR]_2.56-1_amd64.deb) first; and then the specific (cndrvcups-[COLOR="#0000FF"]capt[/COLOR]_2.56-1_amd64.deb) afterwards

2) you cited the CNCUPSLBP3150CAPTK.ppd .............ie > [COLOR="#EE82EE"]sudo /usr/sbin/lpadmin -p LBP3100 -m CNCUPSLBP3150CAPTK.ppd -v ccp://localhost:59787 -E[/COLOR]

3) you used ccp://localhost:59787 .................... the Canon guides suggest ccp://localhost:59687

what does 

> [COLOR="#FF0000"]sudo dpkg -l | grep Canon[/COLOR] give you?

what does

> [COLOR="#FF0000"]sudo service ccpd status[/COLOR]

what does

> [COLOR="#FF0000"]captstatusui -P LBP3100[/COLOR]

There seem to be 4 stages for the LBP install

1) if 64bit, install specific needed 64bit packages
2) install CAPT drivers
3) Register the printer with CUPS (sudo /usr/sbin/lpadmin -p LBP3100 -m CNCUPSLBP3050CAPTK.ppd -v ccp://localhost:59787 -E)
4) Register the printer in the CCPD daemon (sudo /usr/sbin/ccpdadmin-p LBP3100 -o /dev/usb/lp0 )

then start the ccpd daemon > [COLOR="#FF0000"]sudo service ccpd start[/COLOR] ........check its status > [COLOR="#FF0000"]sudo service ccpd status[/COLOR]  and if two numbers, should all be good to go

---

### Post by ernstblaauw on 2013-07-04
Thanks for your help.

[LIST]
[*]I installed the 2.56 drivers one by one in correct order
[*]I used the command  ```
sudo /usr/sbin/lpadmin -p LBP7200Cdn -m CNCUPSLBP7200CCAPTK.ppd -v ccp://localhost:59787 -E
```, as I have a LBP7200Cdn
[*]'sudo dpkg -l | grep Canon' gives two packages:
```
ii  cndrvcups-capt                                              2.56-1                                              Canon CAPT Printer Driver for Linux
ii  cndrvcups-common                                            2.56-1                                              Canon Printer Driver Common Modules Ver.2.56

```
[*]'sudo captstatusui -P LBP7200Cdn' : won't start, on the command line it just shows an empty row and no screen comes up. Only option to exit is ctrl-c.
[*]```
$ sudo service ccpd status
/usr/sbin/ccpd: 2446 1437
```
[*]Printing a test page from 'Printing' dialog does nothing.
[*]Removing or reinstalling the package 's-esp_8.71.dfsg.1-0ubuntu5.5_all.deb' does not make a difference
[/LIST]

Do you have any clue what's happening here? I don't know if printing in 12.04 is different in Linux Mint 13 (Mint 13 is built upon 12.04).

---

### Post by pdc on 2013-07-04
I wonder how your printer is connected

what does 

> [COLOR="#FF0000"]/usr/sbin/lpinfo -v[/COLOR] give you?

eg for my LBP3100 I get (amongst other things........) > direct usb://Canon/LBP3100/LBP3108/LBP3150?serial=0000B18B4GVx

---

### Post by ernstblaauw on 2013-07-06
> **pdc said:**
> I wonder how your printer is connected

what does 

 give you?

eg for my LBP3100 I get (amongst other things........)

I got:
```
direct usb://Canon/LBP7200C?serial=0000A6C6TNgj

```

captstatusui is having a ```
*** captstatusui Socket Error ***
```. Do you know what could be causing this?

---

### Post by pdc on 2013-07-06
**[COLOR="#0000FF"]Question 1:[/COLOR]**
has the printer ever worked using the current install

.........because posts such as this

[http://ubuntuforums.org/archive/index.php/t-1004407.html](http://ubuntuforums.org/archive/index.php/t-1004407.html)

suggest that the command

> [COLOR="#FF0000"]sudo /etc/init.d/ccpd restart[/COLOR]

can sometimes get things going

____________________________________________________________________________________________

by default, the system will assume you only have one printer; and it will be attached by usb to lp0;

**[COLOR="#0000FF"]Question 2[/COLOR]**
do you have more than one printer connected to the computer?

---

### Post by ernstblaauw on 2013-07-08
> **pdc said:**
> **[COLOR="#0000FF"]Question 1:[/COLOR]**
has the printer ever worked using the current install

.........because posts such as this

[http://ubuntuforums.org/archive/index.php/t-1004407.html](http://ubuntuforums.org/archive/index.php/t-1004407.html)

suggest that the command



can sometimes get things going

____________________________________________________________________________________________

by default, the system will assume you only have one printer; and it will be attached by usb to lp0;

**[COLOR="#0000FF"]Question 2[/COLOR]**
do you have more than one printer connected to the computer?
- 'sudo /etc/init.d/ccpd restart' doesn't make a difference, tried that many times.
- It is the only printer connected. Before this one, I had a Canon Ip4x00, but they never were connected together.

So, those answers do not clarify things, I guess. Do you have other ideas? Do other people here get there LBP-printer working on 64-bit?

---

### Post by pdc on 2013-07-08
the devil is in the detail;

I cannot quote chapter and verse of folks who get the 64bit running; I have an LBP running on 32bit; I did another install on an older Mint and it worked fine too

one can only suggest going over the ground again: remove existing install

([COLOR="#EE82EE"]sudo /usr/sbin/ccpdadmin -x LBP7200C[/COLOR]) ............removes from the ccpd daemon.

and 

([COLOR="#EE82EE"]sudo /usr/sbin/lpadmin -x LBP7200C[/COLOR]) .................deletes the printer's spooler registration.

............I quote LBP7200C as that is what your previous printout gave ......

for a fresh install; 
the 64bit preliminary installs;
the CAPT driver install;
register with CUPS;
register the ccpd daemon;
restart the ccpd;
do a test print

---

### Post by ernstblaauw on 2013-07-09
> **pdc said:**
> the devil is in the detail;

I cannot quote chapter and verse of folks who get the 64bit running; I have an LBP running on 32bit; I did another install on an older Mint and it worked fine too

one can only suggest going over the ground again: remove existing install

([COLOR="#EE82EE"]sudo /usr/sbin/ccpdadmin -x LBP7200C[/COLOR]) ............removes from the ccpd daemon.

and 

([COLOR="#EE82EE"]sudo /usr/sbin/lpadmin -x LBP7200C[/COLOR]) .................deletes the printer's spooler registration.

............I quote LBP7200C as that is what your previous printout gave ......

for a fresh install; 
the 64bit preliminary installs;
the CAPT driver install;
register with CUPS;
register the ccpd daemon;
restart the ccpd;
do a test print

Thanks for your help! It is really appreciated. 

I guess this is the 64-bit problem - 32-bit worked fine before where 64-bit failed. So I hope the guy who posted on askubuntu can give some hints about his setup and steps he took to make his printer work.

---

### Post by dheinson on 2013-11-11
Unfortunately, this appears to be broken in 13.10 Saucy Salamander. The ia32-libs package depends on lib32asound2 which has been discontinued in 13.10. I installed the package with a manual override which did not help, and is generally not advisible as it messes up the package cache.  Any suggestions? The best solution would probably be if Canon provided a proper driver...

---

### Post by zKhtdyX on 2013-11-12
hi dheinson,
have you tried canon capt driver version 2.6? They got 64-bit deb packages. But it did not work for me (12.04 64bit). Printer prints nothing :(
[http://support-au.canon.com.au/contents/AU/EN/0100459602.html](http://support-au.canon.com.au/contents/AU/EN/0100459602.html)

---

### Post by dheinson on 2013-11-18
> **zKhtdyX said:**
> have you tried canon capt driver version 2.6? They got 64-bit deb packages.
Of course. Those packages depend on 32-bit-libraries that are no longer included in 13.10 and it will break things to force-install the versions from older ubuntu releases.
> **zKhtdyX said:**
> But it did not work for me (12.04 64bit). Printer prints nothing :(Follow this guide, it is very thorough and worked for me: [http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp) 
You can use Google translator if you do not speak French. Also one thing the guide does not mention is that sometimes it is necessary to turn the printer off and on after starting the ccp daemon to make things work.

Good luck.

---

### Post by superm1 on 2013-11-30
I just got one of these printers with 12.04.  Some comments about getting it setup.

1) Rather than overwriting that 70-printers.rules, just remove the package system-config-printer-udev so that it won't ever be overwritten again.

2) This is the udev file I used to automatically start when plugging it in:
ACTION=="add", KERNEL=="lp*", ATTRS{idVendor}=="04a9", RUN+="/etc/init.d/ccpd start"
KERNEL=="lp*", SUBSYSTEMS=="usb", ACTION=="remove", RUN+="/etc/init.d/ccpd stop"

---

### Post by emmfranklin on 2014-05-27
This is the solution to install canon lbp 3000 printer in a ubuntu 11.10 over a lan 
connection from a computer having windows connected directly to
the printer.
Note the Following models are supported 
LBP2900
LBP3000
LBP3100/3108/3150
LBP3200
LBP3250
LBP3300
LBP3310
LBP3500
im using a ubuntu 11.10 system 32 bit 

you can use my ideas as a base if your actual requirements differ 

64bit is also supported accordingly.

You need to have Gdebi installer istalled in your system to simplify the process
if you dont have then please install Gdebi installer first.
Gdebi installer helps to install deb files.

If you know another way to install deb files you may proceed.

Steps to install Canon printer over a network from another computer
downlad the tar.gz file approx 60 mb

[http://gdlp01.c-wss.com/gds/6/0100004596/03/Linux_CAPT_PrinterDriver_V260_uk_EN.tar.gz](http://gdlp01.c-wss.com/gds/6/0100004596/03/Linux_CAPT_PrinterDriver_V260_uk_EN.tar.gz)
extract it in a folder of your choice name

browse inside 

go to the folder 32bitdriver/debian/
(note 64bit driver is also available in this compressed file )

install capt drivers using gdebi installer


strictly in the following order

cndrvcups-common_2.60-1_i386.deb
cndrvcups-capt_2.60-1_i386

restart linux

start terminal
type
sudo system-config-printer
give password when asked
press add
select network printer
select windows printer via samba
click browse
locate the computer 
click the printer canon lbp3000

click forward

follow the onscreen commands .

you are done

you may print a test page

---

### Post by emmfranklin on 2014-05-27
This is the solution to install canon lbp 3000 (and other related models )printer in a ubuntu 11.10 over a lan 
connection from a computer having windows connected directly to
the printer.

Note the Following models are supported 
LBP2900
LBP3000
LBP3100/3108/3150
LBP3200
LBP3250
LBP3300
LBP3310
LBP3500

im using a ubuntu 11.10 system 32 bit 

you can use my ideas as a base if your actual requirements differ 

64bit is also supported accordingly.

You need to have Gdebi installer istalled in your system to simplify the process
if you dont have then please install Gdebi installer first.
Gdebi installer helps to install deb files.

If you know another way to install deb files you may proceed.

Steps to install Canon printer over a network from another computer
downlad the tar.gz file approx 60 mb

[http://gdlp01.c-wss.com/gds/6/0100004596/03/Linux_CAPT_PrinterDriver_V260_uk_EN.tar.gz](http://gdlp01.c-wss.com/gds/6/0100004596/03/Linux_CAPT_PrinterDriver_V260_uk_EN.tar.gz)
extract it in a folder of your choice name

browse inside 

go to the folder 32bitdriver/debian/
(note 64bit driver is also available in this compressed file )

install capt drivers using gdebi installer


strictly in the following order

cndrvcups-common_2.60-1_i386.deb
cndrvcups-capt_2.60-1_i386

restart linux

start terminal
type
sudo system-config-printer
give password when asked
press add
select network printer
select windows printer via samba
click browse
locate the computer 
click the printer canon lbp3000

click forward

follow the onscreen commands .

you are done

you may print a test page

---

