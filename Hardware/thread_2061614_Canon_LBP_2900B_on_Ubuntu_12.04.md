---
title: "Canon LBP 2900B on Ubuntu 12.04"
date: 2012-09-23
forum: Hardware
---

### Post by balasankarc on 2012-09-23
Hi all,
I am desperately trying to install my Canon LBP 2900B Laser Printer on Ubuntu 12.04... I've gone through [https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190) but had no success... Actually the file "/etc/modprobe.d/blacklist-cups-usblp.conf" is missing in my system... and the folder usb in "/dev"... Can anyone please give me step by step instruction to install my printer?? Please....

---

### Post by pdc on 2012-09-23
so there are two stages:

1) get the drivers installed

2) tell your system about the new printer

1) **_[COLOR="SeaGreen"]DRIVER INSTALL[/COLOR]_**:

how did you go on this? If you go to synaptic, you should get a picture like cndrvcups screenshot that I enclose

........that is when the drivers are installed; *and you need the common package installed first*.........

2) **_[COLOR="SeaGreen"]TELLING YOUR SYSTEM[/COLOR]_**

I like this step; which comes after driver install; from the link you quote

[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

**_[COLOR="Red"]2a) Register the printer:[/COLOR]_**

> sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp://localhost:59787 -E

as by using 

ccp://localhost:59787 .. you don't need fido directories..

then you need to 

**_[COLOR="Red"]2b) Register the printer with ccpd daemon:[/COLOR]_**

> sudo /usr/sbin/ccpdadmin -p LBP2900 -o /dev/usb/lp0 

.........*assuming you only have this one printer, so it gets called lp0*...

then you need to 

 **_[COLOR="Red"]2c) Start ccpd daemon:[/COLOR]_**

> sudo /etc/init.d/ccpd start 

then [COLOR="Red"]2d)[/COLOR] **_[COLOR="Red"]test the install[/COLOR]_**

> captstatusui -P LBP2900 

..that will open the Status Monitor window. 

If the message "Ready to print" is displayed --> all is OK.

**_Try to print something._**!!!!!!!!!

....if the printer kicks into life, great!

My suggestions as to what to do are:

1) first part the ubuntu wiki

and then 

2) this great thread 

[http://ubuntuforums.org/showthread.php?t=1982917](http://ubuntuforums.org/showthread.php?t=1982917)

particularly post #4 by Sivella, who is a great master on the LBP:

......if you subscribe to this thread:

top right: thread tools; 3 down subscribe; and if the above works, we need to set up your system so it works each time!

__________________________-

Actually the file "/etc/modprobe.d/blacklist-cups-usblp.conf" is missing in my system

...........you may not need that step...........

---

### Post by balasankarc on 2012-09-23
> **pdc said:**
> so there are two stages:

1) get the drivers installed

2) tell your system about the new printer

1) **_[COLOR="SeaGreen"]DRIVER INSTALL[/COLOR]_**:

how did you go on this? If you go to synaptic, you should get a picture like cndrvcups screenshot that I enclose

........that is when the drivers are installed; *and you need the common package installed first*.........

2) **_[COLOR="SeaGreen"]TELLING YOUR SYSTEM[/COLOR]_**

I like this step; which comes after driver install; from the link you quote

[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

**_[COLOR="Red"]2a) Register the printer:[/COLOR]_**



as by using 

ccp://localhost:59787 .. you don't need fido directories..

then you need to 

**_[COLOR="Red"]2b) Register the printer with ccpd daemon:[/COLOR]_**



.........*assuming you only have this one printer, so it gets called lp0*...

then you need to 

 **_[COLOR="Red"]2c) Start ccpd daemon:[/COLOR]_**



then [COLOR="Red"]2d)[/COLOR] **_[COLOR="Red"]test the install[/COLOR]_**



..that will open the Status Monitor window. 

If the message "Ready to print" is displayed --> all is OK.

**_Try to print something._**!!!!!!!!!

....if the printer kicks into life, great!

My suggestions as to what to do are:

1) first part the ubuntu wiki

and then 

2) this great thread 

[http://ubuntuforums.org/showthread.php?t=1982917](http://ubuntuforums.org/showthread.php?t=1982917)

particularly post #4 by Sivella, who is a great master on the LBP:

......if you subscribe to this thread:

top right: thread tools; 3 down subscribe; and if the above works, we need to set up your system so it works each time!

__________________________-

Actually the file "/etc/modprobe.d/blacklist-cups-usblp.conf" is missing in my system

...........you may not need that step...........

It worked man....U r great....thanx...how ti setup my system so it works each time?

---

### Post by pdc on 2012-09-23
tremendous!

go here 

[http://ubuntuforums.org/showthread.php?t=1982917](http://ubuntuforums.org/showthread.php?t=1982917)

post #6

Maestro Sivella tells all........

he is french, and maintains the french canon support system; so he has a link at the end of post #6 which you can translate with google

.....but if you just copy and paste the commands he lays out in post #6, I would hope things will go well for you

---

### Post by balasankarc on 2012-09-23
How can i share this printer with another Ubuntu 12.04 system over network via samba??? I can share files, but can't do the same about printer...

---

### Post by pdc on 2012-09-23
I don't know: I use google for such things

[http://lmgtfy.com/?q=share+this+printer+with+another+Ubuntu+12.04+system+over+network+via+samba](http://lmgtfy.com/?q=share+this+printer+with+another+Ubuntu+12.04+system+over+network+via+samba)      :D    :D

Did you get the printer set up so it starts ccpd each time?

the command

> sudo /etc/init.d/ccpd start 

should do it from a terminal.......if needed

---

### Post by vigyani on 2012-10-22
Hi

Thanks.
I am using Ubuntu 12.04.1. Installed and configured Canon LBP 2900B, using this guide and it worked for me.
First it did not work but on restarting CCPD, printer responded and I could print.

> sudo service ccpd restart

regards
Vigyani

---

### Post by maverick555 on 2012-10-22
Which driver version you installed ?
Will this work in 64bit ubuntu ?
Will you write a more detailed guide please like 
1.switch on printer
2.install drivers like this etc....

Please..

---

### Post by pdc on 2012-10-22
> Will this work in 64bit ubuntu ?

...........well............there are NO debian packages for the 64bit system; you need to use alien to convert the rpm packages to deb packages

......as described here......

[http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html)

eg to convert and install the common capt driver, the command would be

> sudo alien -i cndrvcups-common-2.40-1.x86_64.rpm

and then the specific package

> sudo alien -i cndrvcups-capt-2.40-1.x86_64.rpm

........*[COLOR="Green"]**but this would only be after navigating yourself to the correct directory that these files are stored in**[/COLOR]* ........

.........so we can guide you through the 64bit install.........

.........before that.......to install the drivers .......

.this is from the Ubuntu HOW-TO

[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

> For a new install please see the html guide in the 2.4 driver download:

    Download 32/64 Bit Linux CAPT Printer Driver v2.40 English. 

from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0900772424.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0900772424.html)

you will be downloading CAPT Printer Driver for Linux Version 2.40

.....which comes down as Linux_CAPT_PrinterDriver_V240_uk_EN.tar.gz

one needs the correct version of ........

cndrvcups-common.deb     

cndrvcups-capt.deb

.........[COLOR="Red"]*You MUST INSTALL the COMMON DRIVER first*[/COLOR] ........

Install from the v2.40 driver as you would any other package with Ubuntu Software Center. 

..................post #3 above covers the later configuration......

as the process is:

1) install the drivers
2) tell the system about your new printer

---

### Post by xlearner on 2012-11-03
@PDC,

I recently purchased this printer. Thanks for the wonderful guide. I was able to print following the steps outlined by you. 

FYI, I have 32 bit ubuntu 12.04. 

Xlearner

---

### Post by pdc on 2012-11-03
that's great; enjoy

in this thread

[http://ubuntuforums.org/showthread.php?t=1982917](http://ubuntuforums.org/showthread.php?t=1982917)

Sivella, who is very knowledgable on the LBP series,

describes how to automate the process of ensuring the printer is recognised each time you restart the computer;

.........it helps to complete everything so you can enjoy your printer

---

### Post by tonidito on 2012-11-12
Hi,
please follow instructions at the following web page:

[http://ubuntuforums.org/showthread.p...5#post12350075]("http://ubuntuforums.org/showthread.php?p=12350075#post12350075")
(#12)

and You will solve the problem with Canon CAPT printer drivers!

tonidito:razz:

---

### Post by deepla on 2012-11-20
Hi Thanks to pdc and Sivella for solving this problem. I too have this printer and was struggling for sometime dual booting. The solution given here did not seem to work for me at first . But that was becasue I closed the status monitor window saying the "printer is ready" and tried to print. With the window kept open, I was able to print. Thank you so much.
I have ubuntu 12.04 32 bit

---

### Post by sysone on 2012-11-22
nevermind
error

---

### Post by chandraubunt on 2013-04-05
> **balasankarc said:**
> Hi all,
I am desperately trying to install my Canon LBP 2900B Laser Printer on Ubuntu 12.04... I've gone through [https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190) but had no success... Actually the file "/etc/modprobe.d/blacklist-cups-usblp.conf" is missing in my system... and the folder usb in "/dev"... Can anyone please give me step by step instruction to install my printer?? Please....

Hello balasankarc,
         I am also having the same problum  as I have been  strugling to install Canon LBP 2900B laser printer in my 12.04  ubuntu OS(64 bit).I noticed that you have solved your problum from the reply of *pdc*.Would you please explain me the step you intalled your printer ? How you downloaded driver ? Do I need to change my OS from 64 bit to 32 bit system ? please give me a detailed step by step  procedure.

---

### Post by pdc on 2013-04-05
hi chandra;

I think the best guide is this

[http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

it is in french by a chap called Sivella; if you have access to google, you can use the google translate function to convert to whatever language you wish:

you can see the 64bit has quite a few more steps: I think the 32bit is much easier; ............. up to you.................

........I will follow this thread so post back as you need advice, comments.......whatever

---

### Post by chandraubunt on 2013-04-07
Hai pdc
  I am a bigginer in ubuntu so i have little bit  difficulty in  installation proceedure .I am trying  hard to get my printer  work,yet, till now ,not succeeded. Thank you for the reply.

---

### Post by pdc on 2013-04-07
you said before

> Do I need to change my OS from 64 bit to 32 bit system ?

I think YES would be the correct answer............but it is your computer and your system

come back to us when you have a 32bit partition: we can help you further; you can add a 32bit partition and leave the 64bit still installed

---

### Post by chandraubunt on 2013-04-08
I am having  both Windows and Ubuntu in my system. How    a 32 bit partition is added without leaving already installed 64 bit? thank you.

---

### Post by pdc on 2013-04-08
I believe you can just add it

---

### Post by chandraubunt on 2013-06-23
I have changed my  OS to 32 bit,please help me to install lbp2900B canon laser printer

---

### Post by pdc on 2013-06-23
go here and download the CAPT driver

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html)

it comes down as [COLOR="#008000"]Linux_CAPT_PrinterDriver_V256_uk_EN.tar.gz[/COLOR]

I base my advice on Sivella's excellent instructions [http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp) which are in french so use google to translate to your favourite language

1) Install the CAPT drivers

the commands to copy and paste into a terminal are:

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf Linux_CAPT_PrinterDriver_V256_uk_EN.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd Linux_CAPT_PrinterDriver_V256_uk_EN/32-bit_Driver/Debian[/COLOR]

now get the system to list what is in that directory

> [COLOR="#FF0000"]ls[/COLOR]

it should say > [COLOR="#008000"]cndrvcups-common_2.56-1_i386.deb[/COLOR] and [COLOR="#008000"]cndrvcups-capt_2.56-1_i386.deb[/COLOR] 

If so, 

> [COLOR="#FF0000"]sudo dpkg -i cndrvcups-common_2.56-1_i386.deb[/COLOR]

and then

> [COLOR="#FF0000"]sudo dpkg -i cndrvcups-capt_2.56-1_i386.deb[/COLOR]

> [COLOR="#FF0000"]sudo service cups restart[/COLOR]

2) register the printer in CUPS

> [COLOR="#FF0000"]sudo /usr/sbin/lpadmin -p LBP2900B -m CNCUPSLBP2900CAPTK.ppd -v ccp://localhost:59787 -E[/COLOR]

3) register the printer with the ccpd daemon

first let's check where the computer "sees" your printer is connected

issue the command

> [COLOR="#FF0000"]/usr/sbin/lpinfo -v[/COLOR]

you will get maybe ten lines of results printed in your terminal 

do you see [COLOR="#0000FF"]direct usb:/dev/usb/lp0[/COLOR] somewhere in the list            .........if you do, we use the [COLOR="#008000"]/dev/usb/lp0[/COLOR] portion .............

> [COLOR="#FF0000"]sudo /usr/sbin/ccpdadmin -p LBP2900B -o /dev/usb/lp0[/COLOR]

now start the ccpd daemon

> [COLOR="#FF0000"]sudo service ccpd start[/COLOR]

now check it works

> [COLOR="#FF0000"]sudo service ccpd status[/COLOR]

you should get something like

> [COLOR="#0000FF"]Canon Printer Daemon for CUPS: ccpd: 8956 8954[/COLOR]

now try to print something .........if it works..........you can automate starting the ccpd daemon as Sivella describes [http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

...........if we get you that far, is that helpful?

---

### Post by chandraubunt on 2013-07-17
Dear PDC ,
              thank you very much for the help.Sorry for being late to reply I was little bit busy.let me try it 
                                                                                                                    -  Chandra

---

### Post by chandraubunt on 2013-07-20
[SIZE=4]Hello dear  Pdc,
[/SIZE]
[SIZE=4] [/SIZE][SIZE=4]                     ... succeeded  ...... with the great help of  you  !!     Now I could  print with my LBP2900B !![/SIZE]
[SIZE=4] [/SIZE][SIZE=4] Thank you very much for the help. How genorous of you to help me  by giving  detailed instructions  . It is a great site that there will be a solution for every thing in  computer world.
                                                                                 
                                                                                                  - Chandra[/SIZE]

---

### Post by chandraubunt on 2013-07-31
Now Icould print but have to run the commands,   [COLOR=#ff0000]sudo service ccpd start [/COLOR] 
 [COLOR=#ff0000]sudo service ccpd status[/COLOR]

 in terminal every time when switched on the computer.

---

### Post by EBWQNHD on 2013-08-02
thanks for your earlier, very kind comments about helping; I was very pleased the printer worked for you;

............ to get it to work each time, 

read Sivella's post .............. the original is in French so translate with Google as suits you to your favourite language;

he details how to automate things so the LBP works each time

it is **section 3.3** in his post

let us know if it is not clear and we can offer further help

---

### Post by srdjan2 on 2014-07-10
Hi friends, so it looks that there is a new version of CAPTA driver from may 2014 (link you offered for downloading), and this lovely instructions are not valid any more....at least for me ... I can not install lbp 2900 on ubuntu 12.04 LTS (64-bit). Here it is what is going on:

After the command: [COLOR=#FF0000]*/usr/sbin/lpinfo -v / *[/COLOR]result is: [COLOR=#ff0000]direct usb://Canon/LBP2900?serial=0000A266LF4T   [/COLOR] I can not proceed further ... Also, I tried those instructions from "French" link .... no success. Just to notice that system recognize the printer (two of them) but I can not print a Test page. Here is the answer:[COLOR=#ff0000] Idle - ccp send_data error, exit[/COLOR]. 
[COLOR=#ff0000][/COLOR]
Thank you in advance for your help to the newcomer :)

---

### Post by pdc on 2014-07-10
sorry to hear of your issues: .....sounds like you have a new install of 12.04 .........if you want the printer to work, some might suggest you install a 32bit version of 12.04 and the LBP will work well; (for what it's worth, we have 12.04 32bit and our LBP installed quickly and well)

12.04; as you will know; is supported till 2017; a nice stable platform

---

