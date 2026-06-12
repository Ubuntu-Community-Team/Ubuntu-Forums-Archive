---
title: "Can't install Jaunty"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by McChubs on 2009-04-30
Alright, well 8.10 failed to install, but no problem, I'm not a quitter. Take two: I burned Jaunty onto a disc, restarted, ran its installer and sure enough, a promising little loading bar appeared. After a little while, it finished doing that and simply dumped me to a DOS-style page, as if it was waiting for a command. Now if this was MS-DOS I'd probably have a better chance of finding out what was going on, but in Linux I'm basically stuffed. Same thing happened with 'run without affecting your PC'. What's going on?

---

### Post by N_Nick on 2009-04-30
It would be really helpful to know what kind of prompt you are at, if you are at a login prompt you can just login with your username/password and type > startx

But again we cant really help until you give us more information

---

### Post by yoasif on 2009-04-30
try the alternate install cd. 

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by lisati on 2009-04-30
Welcome to the team, and don't be too quick to give up.

A couple of things to check: did you get an option to "check disks for defects" before your ran the installer? Were you able to run the "Live CD"?

---

### Post by McChubs on 2009-04-30
I'm not sure what you mean by Live CD; do you mean the 'Run Ubuntu without affecting my PC' option? That brought up the same result, a friendly little loading bar and then this prompt page which invites me to type 'help' for more commands. They don't really mean anything to me though, so that's not actually all that helpful.

---

### Post by McChubs on 2009-04-30
I checked the disc's integrity and we are, apparently, all good. Virtual Box also runs the disc fine: it ran the 'Run Ubuntu without...' option without any complaining. I can't work out why Ubuntu's getting upset with a 'real' installation, but it's happy in Virtual Box. Installing it properly doesn't bring up a prompt or any GUI, it's literally like a DOS window, as if something's gone wrong and it expects me to sort it out.

---

### Post by PRchrdsn on 2009-04-30
I have a Dell Inspiron 2650 w/256MB of memory.  Ubuntu 8.10 has installed and worked fine.  Tried the upgrade to 9.04 from the Upgrade Manager, and waited through HOURS of download and install.  Proceeded without reported error up to the point where it needed a reboot to finish the installation.  Upon the reboot, the boot process hung on the screen that indicated that it would boot from the hd.    I downloaded the .iso file and burned it to a CD.  Booting from the CD, the menu shows up.  Selecting 'Install Ubuntu' produces some disc activity on the CD drive, the screen then goes blank and the disc activity stops.  Nothing happens from that point on.  Hung again.  Any ideas?      TIA, Paul  p.s., Any idea how to get the Preview to recognize a CRLF?  Can't seem to break message into paragraphs.

---

### Post by McChubs on 2009-04-30
Alright, when I try to install/use the CD 'live', it has the little side-to-side loading bar thing, then comes on a black screen. 'Loading in progress...' is at the top, and the command prompt is called Busybox. The command lines are prefixed by initram). If no one has any ideas, I'll try the alternative version, and if that doesn't work I guess the only option is an in-Windows install.

---

### Post by trash on 2009-04-30
I spent about 3 days trying different versions... in the end what worked was to install (F4) a commandline system and then apt-get install ubuntu-desktop.

The Jaunty full and alternate always gave me disc errors when scanned and any other type of install would fail.. i think even the memory scans failed.. I swear i tried everything before going with the commandline system. I am now running Jaunty without any problems. good luck!

---

### Post by McChubs on 2009-04-30
Wait, can you put that in simple, I-don't-know-what-you-just-said English? That sounds pretty promising.

---

### Post by McChubs on 2009-04-30
FML. I tried doing the alternate CD/command line install, only to be cheerily told I didn't have a common CD drive (I'm not sure what the installation programme thought I was running off -- maybe Uri Geller was transmitting the data by telepathy). Not to be beaten, I switched CD drives, and same again. Hurray! When a man finds himself unbending safety pins to push the bay door out of his CD drive at 4am because it's circa 1998 and made by people of questionable skill, you have to wonder how much further you want to go. Back to square zero then. Any ideas?

---

### Post by trash on 2009-05-01
hey, either it's the full or alternate Jaunty(probably alternate). Thats wierd it have that option on both!!

EDIT:Funny you mention the old cddrive because mine is an older one to and it did cross my mind that it was the problem.. Check what it is detected as, master/slave, primary/seconday. mine is primary/slave but i'm not sure if it should be slave or not.

If you do finally get a commandline installed then do:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-desktop

---

### Post by elricbk on 2009-05-01
Have you done "Data Verification" after burning the disc? I had problem exact like yours (with LiveUSB) &#8212; the solution was in buggy flash drive and write errors. Wrote .img file one more time and LiveUSB works now. So, first you should check your downloaded image for consistency and after that you should check that all was written to usbflash or CD properly. Good luck!

---

### Post by McChubs on 2009-05-01
I'm sure it's not the discs, they work fine in Virtualbox peversely. I've got a 1GB SD card from a digitcal camera and some generic USB card reader, is there any way I could combine this arcane wizardy into installing Ubuntu that way?

---

### Post by elricbk on 2009-05-01
It depends on card reader, I believe. If, combined with SD card, it behaves like usual USB stick, then you can go LiveUSB way. But if it is multi-cardreader (42 in 1 or smth like this) which behaves like multiple disks at once, then it would be problematic. Don't know for sure, though.

UPD: Got my MSI Wind booted from SD card in internal cardreader.

---

### Post by McChubs on 2009-05-01
Ah I went ahead and installed it using Wubi, I'll use LVPM later to make it a 'proper' installation. Kind of a shame I didn't figure out what was wrong, but heyho. It even recognised my monitor and graphics card off the bat, which made me cackle outrageously.

---

