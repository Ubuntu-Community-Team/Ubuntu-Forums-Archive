---
title: "HELP - No CD installation"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by kwhip3 on 2009-01-29
**TOTAL NEWBIE**: I have done some reading and this has been addressed many ways but none seem to directly address my situation. First I am installing on a ToughBook w/ _no CD _& _no network_, _unbootable USB _and only a FDD and a brand new HDD. I can physically remove the HDD and connect it to another computer (via a PCMCIA adapter) where Windows recognizes it. 

Where do I go from here? How can I create a bootable HDD without affecting the existing system? Is there a way to copy the Ubuntu onto the new HDD so I can boot the drive and then install from the new HDD? What about creating a bootable linux FDD w/ usb driver so I can connect to an external CD?

I really need someone to babystep me through this.

---

### Post by icheyne on 2009-01-30
Wubi might be your best bet - [http://wubi-installer.org/](http://wubi-installer.org/).

---

### Post by kwhip3 on 2009-01-30
icheyne: Thanks but I guess I need to elaborate a bit more. The system have no OS. I can boot from the FDD but I have no other means of connecting to the computer in its present state. I can physically remove the blank HDD but how can I configure it so it is bootable to the point where I can install Ubuntu?

---

### Post by icheyne on 2009-01-30
That's a tough one. Would this help?

[https://help.ubuntu.com/community/SmartBootManager](https://help.ubuntu.com/community/SmartBootManager)

---

### Post by Neural oD on 2009-01-30
agreed - this is a very tough one - btw is there no way to overide that boot from usb - maybe try googling - maybe there is a way to flash the bios - and get a more up to date one

---

### Post by eilenbeb on 2009-01-30
I remember seeing some tutorials on how to set up a copy of an installation cd on it's own cd-sized partition on a hard drive and booting from it.

This really sounds like your best bet;  after the installation is up and running you will probably want to browse and install additional software from the installer cd anyways.  If you just install to the target drive, you will need networking or a cdrom-drive to install the extras.

Sorry I can't remember where I found the tut's at, but there are several out there.

I know you asked for step by step help, but I'd better leave that up to someone more advanced than myself.

I will add that you would probably want a live-cd to boot the windows system with, so you can partition and format the target drive.  The live-cd will give you a functioning linux system without making changes to the host system, and give you the neccesary tools.

Good luck and hang in there.

---

### Post by boof1988 on 2009-01-30
If you can use another computer (which it seems like you can), one option (I have gotten it to work with Ubuntu (and Xubuntu) 8.04) is the following:
[LIST=1]
[*]Download ubuntu-8.04.2-desktop-i386(or x86_64).iso
[*]Download and install Unetbootin to a working computer
[*]Create and extra "installer" partition (on the HDD) in addition to the partitions needed for the OS
[*]Use Unetbootin to put the iso file on the "installer" partition and make it bootable
[*]Install HDD into computer, boot up the computer and cross fingers
[*]If computer boots up to "Unetbootin" menu, chose the option for check cd integrity (it has worked for me even though it is actually on a HDD now)
[*]If integrity check returns no errors, let machine reboot and chose either the *try OS* or *install OS* options.
[*]Cross fingers and enjoy.
[/LIST]

This process has worked for me.  I don't know if it will work in your case or not.  Ask any questions if you need anything clarified.

EDIT:

Here's another [thread](http://ubuntuforums.org/showthread.php?t=1035799) with info that might be helpful.

---

### Post by icheyne on 2009-01-30
Good one boof1988.

I put that howto on the wiki - [https://help.ubuntu.com/community/Installation/FromImageLoadedOnHardDrive](https://help.ubuntu.com/community/Installation/FromImageLoadedOnHardDrive)

---

### Post by kwhip3 on 2009-01-31
This looks like the most promising. I was thinking there had to be a way to do this with an ISO but didn't have a clue where to start. I will give it a shot. Thank you for the help.

I also want to thank everyone who responded. Insight of all types help and the more the better.  

:-)

---

### Post by wattsgm on 2009-02-14
We're in the same boat with a couple differences.  My lappy still boots to win2k, but I have no idea how to hook the HD up to another pc.

Also, you appeared to understand the responses offered to far.

So with the differences, does anyone have a suggestion how to load ubuntu (I think xubuntu) with detailed instructions?

toughbook cf-71 PII 366mhz (I think), no cd, FHD, usb, no NIC until the PCMCIA is installed, 

The reason I want to switch OS is I think I can get more life out of this lappy.  With all the patches it lags, and doesn't load some webpages, probably because I've run out of room on the HD to install simple things.  The OS and Avira Anti Virus take up the entire HD.

Many thanks

---

### Post by spcwingo on 2009-02-15
> **wattsgm said:**
> We're in the same boat with a couple differences.  My lappy still boots to win2k, but I have no idea how to hook the HD up to another pc.

Also, you appeared to understand the responses offered to far.

So with the differences, does anyone have a suggestion how to load ubuntu (I think xubuntu) with detailed instructions?

toughbook cf-71 PII 366mhz (I think), no cd, FHD, usb, no NIC until the PCMCIA is installed, 

The reason I want to switch OS is I think I can get more life out of this lappy.  With all the patches it lags, and doesn't load some webpages, probably because I've run out of room on the HD to install simple things.  The OS and Avira Anti Virus take up the entire HD.

Many thanks

You'd be better off installing Puppy on that machine.  I have successfully installed that OS using a CF-72 with no HDD and a USB flash drive.  What I did to achieve this:

1) Pop the Puppy CD into a working computer.
2) Use the Puppy universal installer to install to a flash drive.
3) Those models of Toughbooks don't boot from USB natively, so use wakepup to create a boot floppy.
4) After the install is finished fire up your Toughbook with both the floppy and flash drive inserted.
5) Enjoy!

---

### Post by wattsgm on 2009-02-15
I'd heard of Puppy but saw more about xubuntu.  I'll try and find a floppy (i got went crazy tidying a while back and threw a bunch of stuff out).  Thank you very much.

---

### Post by wattsgm on 2009-02-15
> **spcwingo said:**
> You'd be better off installing Puppy on that machine.  I have successfully installed that OS using a CF-72 with no HDD and a USB flash drive.  What I did to achieve this:

1) Pop the Puppy CD into a working computer.
2) Use the Puppy universal installer to install to a flash drive.
3) Those models of Toughbooks don't boot from USB natively, so use wakepup to create a boot floppy.
4) After the install is finished fire up your Toughbook with both the floppy and flash drive inserted.
5) Enjoy!

I'm making progress...Typing this from Puppy now (on desktop). You said use wakepup.  Considering the age of my toughbook, should I use 'wakepup' or 'wakepup2'? 

My desktop does not have a floppy, so I'll have to copy wakepup_ onto my usb flash, then copy to FHD on my toughbook.  See any problems with this?

This is neat.  thanks.

---

### Post by spcwingo on 2009-02-15
> **wattsgm said:**
> I'm making progress...Typing this from Puppy now (on desktop). You said use wakepup.  Considering the age of my toughbook, should I use 'wakepup' or 'wakepup2'? 

My desktop does not have a floppy, so I'll have to copy wakepup_ onto my usb flash, then copy to FHD on my toughbook.  See any problems with this?

This is neat.  thanks.

If you installed Puppy 2.0 or later, wakepup2.

---

### Post by kwhip3 on 2009-02-21
:D
Wanted to let everyone know the ISO to the HDD partition worked!

Thanks to all!
:D

---

