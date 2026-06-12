---
title: "Canon MF211 on Ubuntu 16.04 32bit not printing"
date: 2017-02-09
forum: Hardware
---

### Post by wmonref on 2017-02-09
Hello! 

I recently installed 16.04, 32 bit and downloaded all the updates.
Installed the latest Canon UFR II v3.30 drivers according to the instructions from [https://wiki.debian.org/PrinterDriver/Canon/UFR-II#Obtaining_the_UFR_II.2FUFRII_LT_Printer_Driver](https://wiki.debian.org/PrinterDriver/Canon/UFR-II#Obtaining_the_UFR_II.2FUFRII_LT_Printer_Driver)

Everything went ok, the system saw the printer as Canon MF 210 series, it picked the corresponding diver and installed it. 
BUT I cannot print anything. When i try to print a test page it says that the job is being processed then it disappears from the queue, but nothing prints out...

Please help!

---

### Post by pdc on 2017-02-09
so Canon provide an install script in the latest 3.3 driver; so it should do all that is needed:

can I suggest you delete the existing entry for your MF211 in the PRINTERS folder; and if you are happy to open a terminal (control alt t are the keys to open a terminal);

and if you paste the following commands into the terminal: (*right-click at the prompt in the terminal, and select paste from the options* ..............)

> [COLOR="#FF0000"]cd Downloads[/COLOR]               ........assuming you downloaded and saved [COLOR="#0000FF"]Linux_UFRII_PrinterDriver_V330_uk_EN.tar.gz[/COLOR] into your Downloads folder (I would have got the file from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html) and it was issued on 16th Dec 2016)

> [COLOR="#FF0000"]tar -zxvf Linux_UFRII_PrinterDriver_V330_uk_EN.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd Linux_UFRII_PrinterDriver_V330_uk_EN[/COLOR]

> [COLOR="#FF0000"]sudo ./install.sh[/COLOR]       and that should hopefully work .......... any joy?

---

### Post by wmonref on 2017-02-09
> **pdc said:**
> so Canon provide an install script in the latest 3.3 driver; so it should do all that is needed

Hi and thanks for the reply!
Did what you suggested and it looks like there are some dependencies missing...The printer still does not print.
Attaching the log from where the red lines begin:

```
: 

Unable to locate package libbeecrypt7:i386

#----------------------------------------------------#
# Install Package Check
#----------------------------------------------------#
 Replace: libbeecrypt7:i386 -> libgcrypt20:i386

#----------------------------------------------------#
# apt-get install
#----------------------------------------------------#
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgcrypt20:i386 is already the newest version (1.6.5-2ubuntu0.2).
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cndrvcups-common : Depends: libpango1.0-0 (>= 1.14.8) but it is not going to be installed
 cndrvcups-ufr2-uk : Depends: libpango1.0-0 (>= 1.14.8) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

#----------------------------------------------------#
# Install Package Check
#----------------------------------------------------#
 OK: libgcrypt20:i386

#----------------------------------------------------#
# apt-get install
#----------------------------------------------------#
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libbeecrypt-dev:i386

#----------------------------------------------------#
# Install Package Check
#----------------------------------------------------#
 Replace: libbeecrypt-dev:i386 -> libgcrypt20-dev:i386

#----------------------------------------------------#
# apt-get install
#----------------------------------------------------#
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgcrypt20-dev:i386 is already the newest version (1.6.5-2ubuntu0.2).
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cndrvcups-common : Depends: libpango1.0-0 (>= 1.14.8) but it is not going to be installed
 cndrvcups-ufr2-uk : Depends: libpango1.0-0 (>= 1.14.8) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

#----------------------------------------------------#
# Install Package Check
#----------------------------------------------------#
 OK: libgcrypt20-dev:i386

#----------------------------------------------------#
# Install Printer Driver (dpkg -i -G --force-overwrite)
#----------------------------------------------------#
(Reading database ... 217121 files and directories currently installed.)
Preparing to unpack .../cndrvcups-common_3.70-1_amd64.deb ...
Unpacking cndrvcups-common (3.70-1) over (3.70-1) ...
dpkg: dependency problems prevent configuration of cndrvcups-common:
 cndrvcups-common depends on libpango1.0-0 (>= 1.14.8).

dpkg: error processing package cndrvcups-common (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cndrvcups-common
(Reading database ... 217121 files and directories currently installed.)
Preparing to unpack .../cndrvcups-ufr2-uk_3.30-1_amd64.deb ...
Unpacking cndrvcups-ufr2-uk (3.30-1) over (3.30-1) ...
dpkg: dependency problems prevent configuration of cndrvcups-ufr2-uk:
 cndrvcups-ufr2-uk depends on libpango1.0-0 (>= 1.14.8).
 cndrvcups-ufr2-uk depends on cndrvcups-common (>= 3.70); however:
  Package cndrvcups-common is not configured yet.

dpkg: error processing package cndrvcups-ufr2-uk (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cndrvcups-ufr2-uk

#----------------------------------------------------#
# cups restart
#----------------------------------------------------#
/etc/init.d/cups restart
[ ok ] Restarting cups (via systemctl): cups.service.


```

Should I try to do what is suggested?

---

### Post by pdc on 2017-02-09
I would indeed; (systems all used to be 32bit; but now we seem to moving to where 64bit is the standard; and using 32bit leaves one as the exception and needing extra bits ......... that is just my perception ........... others may chip in and say I have got it wrong .......)

looks to me like you need quite a few little lib files: hopefully the instructions you posted are easy to follow; when I check on my system, it has libpango1.0-0 installed and I have libgcrypt20:i386 and libgcrypt20 already installed; no action on my part!! so you should find these in Synaptic, the package manager

once you get those dependencies installed, if you run the install script again; and watch it; it will hopefully complete for you; by chance I have just run an install script for a Canon inkjet; an older one so libtiff4 was needed; once I installed that tiny file; the install script ran to completion; whereas first time it stopped to tell me what I needed; but as it nears completion (with satisfied dependencies!!), it asks you to verify things; eg usb or network connection; .... correct name ....... you can it what you want ....... etc

---

### Post by wmonref on 2017-02-11
> **pdc said:**
> I would indeed; 

Everything is ok now.! I did not have to install those missing dependencies. I just restarted the comp and the printer once more, then selected A4 as the paper type and everything works now! Thanks a lot, pdc!

But there is one `BUT`. I cannot scan with the standard SimpleScan program... The scanner begins to work when I press the scan button, but then it stops in the middle of the process and on the MF211 screen appears a message that says "scanning has been canceled" and that's it... 
Pease help, again :)

---

### Post by pdc on 2017-02-12
great; glad the printer is working; 

all the various "front-ends" such as Simple Scan, are using SANE as the back-end; the "behind the scenes lifter": 

[http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-CANON](http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-CANON) if you search on the MF210 series devices; which your 211 is part of: they need [COLOR="#0000FF"]testers[/COLOR]!!

so your device needs the guys from the pixmas-5 group: **you have the hardware**: they are the experts to get your scanner going: the linux community would appreciate you helping them; 

so you need to join the sane development mailing list: please feel comfortable with this: they would be delighted to have you contact them: [http://lists.alioth.debian.org/mailman/listinfo/sane-devel](http://lists.alioth.debian.org/mailman/listinfo/sane-devel)

say hello; you have the hardware; these are the experts on scanning to get it working for you: the mailing list is the way they talk to each other

---

