---
title: "canon LBP2900B printer installation 12.04LTS"
date: 2012-07-18
forum: Hardware
---

### Post by chandraubunt on 2012-07-18
I am unable to install Canon LBP 2900B laser jet printer in my lenovo desktop pc , having  os ubuntu 12.04 *Precise Pangolin*. Please  give me detailed steps.

---

### Post by NikTh on 2012-07-18
Hi , 
i can see you device listed here --> [https://help.ubuntu.com/community/CanonCaptDrv190#Ubuntu_12.04_Install](https://help.ubuntu.com/community/CanonCaptDrv190#Ubuntu_12.04_Install) , but not for 12.04 . 
It might worth to give a shot. 
Try to install driver as described on "Ubuntu 12.04 Install" section.
Thanks

---

### Post by chandraubunt on 2012-07-18
> **NikTh said:**
> Hi , 
i can see you device listed here --> [https://help.ubuntu.com/community/CanonCaptDrv190#Ubuntu_12.04_Install](https://help.ubuntu.com/community/CanonCaptDrv190#Ubuntu_12.04_Install) , but not for 12.04 . 
It might worth to give a shot. 
Try to install driver as described on "Ubuntu 12.04 Install" section.
Thanks
Thank you very much,  let me try and see the result.

---

### Post by NikTh on 2012-07-18
Hi , 
please post back the results of your tests here (do not sent pm) , so let other people (more experienced) to know if this worked for you or not.
Maybe they have something else to suggest you. 
Thanks

---

### Post by chandraubunt on 2012-07-18
Hai,

I tried to install  the driver from here _ [https://help.ubuntu.com/community/CanonCaptDrv190#Ubuntu_12.04_Install](https://help.ubuntu.com/community/CanonCaptDrv190#Ubuntu_12.04_Install)  _,but it wont work.There was no driver for 12.04 *Precise Pangolin*. I downloaded  another driver from  here  _[https://github.com/raducotescu/Canon...tarball/master](https://github.com/raducotescu/Canon...tarball/master)_ and installed as  per the information from    "Ubuntu Forums > The Ubuntu Forum Community > Main Support Categories >
Hardware & Laptops
How to install the Canon LBP2900i printer in Ubuntu 12.04 LTS", a post by  **stevecook **.  After  completing all steps  , when I try to print , it shows a error message  like this  "There is a missing print filter for printer canon LBP 2900".

---

### Post by PBKN on 2012-08-31
Is any one solved this issue.

---

### Post by pdc on 2012-09-02
if you have an LBP2900 and are thinking of installing the driver to use it on ubuntu, if I can offer some comments?

if you have 32bit ubuntu, ...good....life is always more sure with that..

the 2900 needs to find the CNCUPSLBP2900CAPTK.ppd on your system

so if you start here

[https://help.ubuntu.com/community/CanonCaptDrv190#Ubuntu_12.04_Install](https://help.ubuntu.com/community/CanonCaptDrv190#Ubuntu_12.04_Install)

you need to download and install

1) the **COMMON** driver first and then

2) the **CAPT** driver

if you click to download, gdebi installer is likely to jump in and offer to install: I suggest accepting this kind offer

then next step would be

> sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp://localhost:59787 -E

and then continue as the ubuntu guide

Sivella in post #4 here

[http://ubuntuforums.org/showthread.php?t=1982917](http://ubuntuforums.org/showthread.php?t=1982917)

is very expert; 

the newer way; of > ccp://localhost:59787

saves the older methodology of needing ccpd, and ccpd/fifo0 and captmon directories..............

it is a bit fiddly getting the LBP going but a great pleasure when it prints!

If you SUBSCRIBE to the thread (know how?) ........ everyone can respond more quickly

---

### Post by ryngkhang on 2012-09-06
Hi 

Well I too have been trying to get my printer up and going. I found a line where one has remove the blacklisting of usb port
from /etc/modprobe.d/blacklist-cups-usblp.conf

> # cups talks to the raw USB devices, so we need to blacklist usblp to avoid
# grabbing them
#blacklist usblp

however when I opened that file there was nothing in it.

could anyone show me how /etc/modprobe.d/blacklist-cups-usblp.conf file looks like, I mean their original contents.

Thanks

---

### Post by ryngkhang on 2012-09-06
Hi Again

Nevermind guys, I just got my printer to print my first test page. 

Thanks Again for all the links.

---

### Post by chandraubunt on 2012-09-08
Please give the details of subscribing a thread.
  Thanks.

---

### Post by pdc on 2012-09-08
gp to the line above the first post (ie #1)

thread tools is the one to head for; click on it; go down three

subscribe to thread: instant notification by email works well for many

---

### Post by maverick555 on 2012-09-11
I have the same printer and i am dual booting with windows just for the printer.
This is a very popular printer,ubuntu should make a driver for this.

---

### Post by pdc on 2012-09-12
um; canon supply the capt driver for the lbp series; for some, it works well

---

### Post by snishanth512 on 2013-08-28
I downloaded the drivers from the canon website.

I installed common.deb and CAPT.deb.

Its not working for me.

Should the printer be disconnected while doing the procedure ???

---

### Post by pdc on 2013-08-29
as well as installing the Canon CAPT printer driver, one needs to do a few more things 

[http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

if you use google translate for the above article in French, you can see what is needed

_______________________________

in this thread, in posts #5 and #9

[http://ubuntuforums.org/showthread.php?t=2168759&highlight=Canon+printer](http://ubuntuforums.org/showthread.php?t=2168759&highlight=Canon+printer)

I have outlined the steps that are needed:

crucially are you using 32bit ubuntu?

_________________________________________

I have an LBP3100B that works well; the Canon CAPT driver does work

__________________________________________

if you have a read at the two threads I mention above; and post back as and when you need more advice

---

### Post by sm2 on 2013-09-06
> go here and download the CAPT driver

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html)

it comes down as Linux_CAPT_PrinterDriver_V256_uk_EN.tar.gz

I base my advice on Sivella's excellent instructions  [http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp) which are  in french so use google to translate to your favourite language

1) Install the CAPT drivers

the commands to copy and paste into a terminal are:


cd Downloads


tar -zxvf Linux_CAPT_PrinterDriver_V256_uk_EN.tar.gz


cd Linux_CAPT_PrinterDriver_V256_uk_EN/32-bit_Driver/Debian

now get the system to list what is in that directory


ls

it should say 
cndrvcups-common_2.56-1_i386.deb and cndrvcups-capt_2.56-1_i386.deb 

If so, 


sudo dpkg -i cndrvcups-common_2.56-1_i386.deb

and then


sudo dpkg -i cndrvcups-capt_2.56-1_i386.deb


sudo service cups restart

2) register the printer in CUPS


sudo /usr/sbin/lpadmin -p LBP2900B -m CNCUPSLBP2900CAPTK.ppd -v ccp://localhost:59787 -E

3) register the printer with the ccpd daemon

first let's check where the computer "sees" your printer is connected

issue the command


/usr/sbin/lpinfo -v

[COLOR=#ff0000]you will get maybe ten lines of results printed in your terminal 

do you see direct usb:/dev/usb/lp0 somewhere in the list             .........[/COLOR]if you do, we use the /dev/usb/lp0 portion .............


sudo /usr/sbin/ccpdadmin -p LBP2900B -o /dev/usb/lp0

now start the ccpd daemon


sudo service ccpd start

now check it works


sudo service ccpd status

you should get something like


Canon Printer Daemon for CUPS: ccpd: 8956 8954

now try to print something .........if it works..........you can  automate starting the ccpd daemon as Sivella describes  [http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

...........if we get you that far, is that helpful?

My greetings to all .
I am new to Ubuntu and I am using 12.04 LTS for couple of months , but never been able to install Printer - Canon LBP2900.
Seen this post above by pdc . But I am not through yet .
I [COLOR=#ff0000][/COLOR]can not see the part marked in red[COLOR=#ff0000] direct usb:/dev/usb/lp0 somewhere in the list             .........[/COLOR]

I may explain what I did :
downloaded the Linux_CAPT_PrinterDriver_V260_uk_EN.tar.gz  Unzipped the folder and installed the Common and CAPT parts in that order , using Ubuntu Software Centre . That was perhaps a mistake . But since I did not know how to uninstall these two , I , without uninstalling these two installations , followed the post by pdc , given above . But I am stuck at point mentioned above . Kindly guide me .

---

### Post by sm2 on 2013-09-06
this is what the terminal is showing :
> sm@sm-desktop:~$ cd Downloads
sm@sm-desktop:~/Downloads$ tar -zxvf Linux_CAPT_PrinterDriver_V260_uk_EN.tar.gzLinux_CAPT_PrinterDriver_V260_uk_EN/
Linux_CAPT_PrinterDriver_V260_uk_EN/32-bit_Driver/
Linux_CAPT_PrinterDriver_V260_uk_EN/32-bit_Driver/Debian/
Linux_CAPT_PrinterDriver_V260_uk_EN/32-bit_Driver/Debian/cndrvcups-capt_2.60-1_i386.deb
Linux_CAPT_PrinterDriver_V260_uk_EN/32-bit_Driver/Debian/cndrvcups-common_2.60-1_i386.deb
Linux_CAPT_PrinterDriver_V260_uk_EN/32-bit_Driver/RPM/
Linux_CAPT_PrinterDriver_V260_uk_EN/32-bit_Driver/RPM/cndrvcups-capt-2.60-1.i386.rpm
Linux_CAPT_PrinterDriver_V260_uk_EN/32-bit_Driver/RPM/cndrvcups-common-2.60-1.i386.rpm
Linux_CAPT_PrinterDriver_V260_uk_EN/64-bit_Driver/
Linux_CAPT_PrinterDriver_V260_uk_EN/64-bit_Driver/Debian/
Linux_CAPT_PrinterDriver_V260_uk_EN/64-bit_Driver/Debian/cndrvcups-capt_2.60-1_amd64.deb
Linux_CAPT_PrinterDriver_V260_uk_EN/64-bit_Driver/Debian/cndrvcups-common_2.60-1_amd64.deb
Linux_CAPT_PrinterDriver_V260_uk_EN/64-bit_Driver/RPM/
Linux_CAPT_PrinterDriver_V260_uk_EN/64-bit_Driver/RPM/cndrvcups-capt-2.60-1.x86_64.rpm
Linux_CAPT_PrinterDriver_V260_uk_EN/64-bit_Driver/RPM/cndrvcups-common-2.60-1.x86_64.rpm
Linux_CAPT_PrinterDriver_V260_uk_EN/Doc/
Linux_CAPT_PrinterDriver_V260_uk_EN/Doc/guide-capt-2.6xUK.tar.gz
Linux_CAPT_PrinterDriver_V260_uk_EN/Doc/LICENSE-captdrv-2.60E.txt
Linux_CAPT_PrinterDriver_V260_uk_EN/Doc/README-capt-2.6xUK.txt
Linux_CAPT_PrinterDriver_V260_uk_EN/Src/
Linux_CAPT_PrinterDriver_V260_uk_EN/Src/cndrvcups-capt-2.60-1.tar.gz
Linux_CAPT_PrinterDriver_V260_uk_EN/Src/cndrvcups-common-2.60-1.tar.gz
sm@sm-desktop:~/Downloads$ cd Linux_CAPT_PrinterDriver_V260_uk_EN/32-bit_Driver/Debian
sm@sm-desktop:~/Downloads/Linux_CAPT_PrinterDriver_V260_uk_EN/32-bit_Driver/Debian$ ls
cndrvcups-capt_2.60-1_i386.deb  cndrvcups-common_2.60-1_i386.deb
sm@sm-desktop:~/Downloads/Linux_CAPT_PrinterDriver_V260_uk_EN/32-bit_Driver/Debian$ sudo dpkg -i cndrvcups-common_2.60-1_i386.deb
[sudo] password for sm: 
(Reading database ... 337180 files and directories currently installed.)
Preparing to replace cndrvcups-common 2.60-1 (using cndrvcups-common_2.60-1_i386.deb) ...
Unpacking replacement cndrvcups-common ...
Setting up cndrvcups-common (2.60-1) ...
sm@sm-desktop:~/Downloads/Linux_CAPT_PrinterDriver_V260_uk_EN/32-bit_Driver/Debian$ sudo dpkg -i cndrvcups-capt_2.60-1_i386.deb
(Reading database ... 337180 files and directories currently installed.)
Preparing to replace cndrvcups-capt 2.60-1 (using cndrvcups-capt_2.60-1_i386.deb) ...
Unpacking replacement cndrvcups-capt ...
Setting up cndrvcups-capt (2.60-1) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
sm@sm-desktop:~/Downloads/Linux_CAPT_PrinterDriver_V260_uk_EN/32-bit_Driver/Debian$ sudo service cups restart
cups stop/waiting
cups start/running, process 2397
sm@sm-desktop:~/Downloads/Linux_CAPT_PrinterDriver_V260_uk_EN/32-bit_Driver/Debian$ sudo /usr/sbin/lpadmin -p LBP2900B -m CNCUPSLBP2900CAPTK.ppd -v ccp://localhost:59787 -E
sm@sm-desktop:~/Downloads/Linux_CAPT_PrinterDriver_V260_uk_EN/32-bit_Driver/Debian$ /usr/sbin/lpinfo -v
direct ccp
network https
network http
direct parallel:/dev/lp0
network lpd
network socket
network ipp
network ipps
network ipp14
file cups-pdf:/
direct hp
network beh
network smb
direct hpfax
sm@sm-desktop:~/Downloads/Linux_CAPT_PrinterDriver_V260_uk_EN/32-bit_Driver/Debian$ 



[COLOR=#ff0000]direct usb:/dev/usb/lp0 [/COLOR]is not there .

I have deleted the printer and tried again after restarting computer . But the result is same again .
In the printing-local host window 2 printers are visible - LBP2900 which is checked , and LBP2900B which is not checked .

---

### Post by pdc on 2013-09-06
my apologies sm2 if I seem to be complicating by going on about lp0

________________________________________________________________

if your LBP printer is connected to a stand-alone computer via a usb cable; and it is the only printer, then the system will call it /dev/usb/lp0 and all will be fine

so by using the command 

> sudo /usr/sbin/ccpdadmin -p LBP2900B -o /dev/usb/lp0

all should be good

so if you make that assumption; and use the above command; if you have the LBP2900 you can move on to the next stage in my instructions; that are directly taken from Sivella

___________________________________________________

It does need to be fastidious to get it working; but you are very much on the right track:

install the drivers common and then the other

if you try the command

> dpkg -l | grep Canon

after installing the drivers, it will tell you if they are there 

eg I get

> ii  cndrvcups-capt  2.40-1 Canon CAPT Printer Driver for Linux
ii  cndrvcups-common 2.40-1 Canon Printer Driver Common Modules Ver.2.40 

for my CAPT driver

__________________________________

if you get it to print once, that is great; and then there is the automatic detection setup needed; happy to guide you through that but the Sivella guide 

[http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

has all the details

---

### Post by sm2 on 2013-09-07
dear pdc ,
I appreciate your quick response to my query . Great .
I am going to try it further and then will return with a feed-back.

---

