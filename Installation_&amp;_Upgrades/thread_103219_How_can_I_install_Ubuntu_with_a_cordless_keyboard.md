---
title: "How can I install Ubuntu with a cordless keyboard?"
date: 2005-12-13
forum: Installation &amp; Upgrades
---

### Post by kevvyd on 2005-12-13
Hi all,

Sorry for the cross-post. I originally put this in the beginner section, but maybe it belongs here...

First off, I'm new to Ubuntu, but have some experience with other Linux distributions in my not-so-recent past (RedHat and Slackware). After working dominantly in the Micro$oft world for some years now I want to babystep my way into open source.

I have sitting by my keyboard at home a Ubuntu 5.10 disk kindly given to me by a friend. I have a nearly-new machine with three hard drives - two of which are set up to run XP, and a third shiny new one that I would like to put Ubuntu on. I'm all geared up, I have home brew that is just the right age to start cracking and the kids are in bed at 7:30, so everything should be set for installation, right?

Not so, at least not yet. It turns out that my cordless mouse/keyboard combo (LogiTech MX700) is not active after the BIOS screen flashes by during the boot phase, so that when the Ubuntu login screen pops up, I can't hit <Return> to continue. Talk about a stumbling start!

I've done some googling and searched this forum and found lots of info on how to get the keyboard up and running once the installation is complete, but I can't find anything to get me past that first <Return>. Has anyone else had to deal with this, and if so, what did you do?

I could, I suppose, borrow a corded mouse/keyboard for the installation, but that somehow seems insufficiently foolhardy. Any ideas?

Thanks,

Kev

---

### Post by matthew on 2005-12-13
I have a cordless MS keyboard that was recognized by the install disk immediately at the beginning of the install process. Your experience with the Logitech may end up being similar.

Edit: What that means is that I didn't have to do ANYTHING to install. Even the first <return> was fine.

---

### Post by Joey French on 2005-12-13
Huh? My cordless mouse and keyboard worked during the install. 

What's up with that? Is it USB?

---

### Post by Zimmer on 2005-12-13
Enter the BIOS by doing a restart after initially booting xp (you should have a working keyboard that way) and see if there are options for enabling BIOS USB support (this is assuming that the cordless keyboard is  USB  device). Had a similar problem with a new cordless for my xp/dual boot box, solved it that way...)


Zimmer

---

### Post by kevvyd on 2005-12-13
Matthew,

It is quite possible, but I can't even start the process. I get to the pretty 
"Ubuntu" screen and it say at the bottom of the screen "For the default installation, press ENTER". I can't press anything, so I can't go anywhere from there.

It is very frustrating and strange. 

Kev

---

### Post by kevvyd on 2005-12-13
Zimmer,

Okay, I'll give the BIOS a try. Thanks!

Geez, you guys are fast! I think I'm going to like this stuff once I get it going.

Kev

---

### Post by greenwom on 2005-12-13
once your in your mouse and keyboard 'extras' may not work 

if you didn't know (I didn't)
sudo dpkg-reconfigure xserver-xorg    will allow you change some settings 

and the config info is in 
/etc/X11/xorg.conf

I'm a newbee but I'll pass what little I know.

---

### Post by kevvyd on 2005-12-13
Alright, thanks Zimmer, the change to the BIOS worked like a charm. Unfortunately, another hiccup walked in afterward. For whatever reason, the installation can't mount the CD drive. Any ideas? It's weird, the CD is obviously being read as I'm booting from it...

greenwom - thanks for the tip. Once I get that far I'll need it for sure.

---

### Post by greenwom on 2005-12-13
EDIT: (i misread)
Again blind leading the blind here 
does it automount in gnome?
or are you trying from a terminal?  

check your fstab 
it's in the /etc

RUN: nano /etc/fstab

This is what mine looks like
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda2       /media/ipod     vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8	0	0

you should be able to go into the /media directory and then:
mount cdrom (you may have to try cdrom0 or cdrom1)

--hope I'm not to far off.

---

### Post by kevvyd on 2005-12-14
greenwom,

I'm going to really show my rookie stripes here, but here goes.

Is gnome the installation package? If so, then no, it does not automount, though it tries. During the installation I go through the select language step and a couple of others and then it tries to mount the CD. at this point it hangs for a while and then comes back and tells me that it can't mount the CD. This strikes me as strange, because it is booting off of the CD and reading off of the CD up to that point, so the CD is okay to there. 

I have tried this several times with a CDs that I burned using Nero and the ISO Recorder Power Toy (XP), as well as a shippit CD, but each time the same thing happens. 

Can I use your suggestion during the actual installation stage, or is that something that I should do after I get through this in order to make sure it mounts correctly later?

Thanks for your help and time!
Kev

---

### Post by greenwom on 2005-12-14
Gnome is the window environment, I Believe that your talking about the 'slash' screen from the install cd.  

To test the CD during the install
choose 'go back' at first opportunity, then scroll down and do a cd test.
EDIT: actually I also believe that there may be a cd test in the boot options.  When you get   
        to the Ubuntu splash screen and it tells you to hit 'enter' read the options F2, F3.  There may 
        be a option to test the CD there.  or try the 'expert' option and see if you can get to that  
        menu earlier.

if the cd fails then burn the cd again at the slowest speed.

When I first tried running my first warty cd it would start the install and then hang.
Someone told me to burn it on a slower speed (1x) and then it worked.  but rerun the install and test your cd first.

Since this has happened on multiple cds I wonder if it's a hardware issue.  Do you have more than one CD/ DVD drive?  This is just a guess, if you have two drives maybe the install software is looking at the primary dive and then not seeing the cd it's looking for.  I know this is a far stretch but I had problems booting from my CD/DVD-RW but I could use the other CD drive.  Shot in the dark.  Hopefully a knowledgeable caffeine addict will respond to your need.

---

### Post by kevvyd on 2005-12-14
Thanks for the tip about testing the CD, greenwom. I'll do that when I get home. I strongly suspect that's the problem but don't know for sure. I only have one CD drive, so there should be no confusion on that score. 

I'll let you know how it goes. 

Again, thanks. 
Kev

---

### Post by Roobert on 2005-12-14
Hey Kev,

Sorry to crash your post, it's Eric. Not bad tech support around here, eh? ;)  I meant to drop by the staff party at lunch, but got swamped. Let me know how the install goes!

---

### Post by kevvyd on 2005-12-16
Roobert - Hey Eric, how is it going? 

Okay, here is the update - I got Ubuntu installed and I am now posting my first message from within it! 

It turns out that my problems had to do with my BIOS setup, which I think I should have guessed from the outset. I got poking around in there and it turned out that I had not properly set my ATA and SATA settings when I put in the new harddrive on the weekend. 

Thanks a lot for the help, greenwom and Zimmer! I suspect I'll be a regular around here now that the adventure turns to installing new software and such.

Kevout

---

