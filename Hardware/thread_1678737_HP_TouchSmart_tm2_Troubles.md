---
title: "HP TouchSmart tm2 Troubles"
date: 2011-01-30
forum: Hardware
---

### Post by yelojakit on 2011-01-30
Hi all,

I know the title is a bit broad but I cannot exactly pinpoint my problem. The more I was trying to fix it, the more I realized it may not be just one problem. It does narrow down to ATI gpu and/or missing partition though.  So, I'm going to just try and tell you all as much detail as to what happened and hope that I can get some help.

What happened:
Anyways, I recently installed Ubuntu 10.04 as a dual boot on the HP TouchSmart tm2, it is using Windows 7 and is 64 bit.  Everything was fine as I was writing some code when I realized I needed to save to my Windows partition (well, I didn't need to but I couldn't get the code simulator to work in Ubuntu).  But, I couldn't find it.  After some googling, I found that I may need to mount the harddrive and it recommended me some software.  Unfortunately, I cannot remember the name of it for the life of me.  Anyways, I tried mounting my largest partition, which I knew to be my C drive in windows but I still couldn't access it.  I unmounted and it still didn't work.  I somehow later found that I could access it under a different name that had a bunch of boot files and etc.

I kept getting this update to do something about getting software for my hardware.  Before installing Ubuntu i remembered reading something about the ATI Graphics card, which is what the alert was about.  So I installed it (I know, my big mistake there).  Now, when I boot into Ubuntu I get to the Ubuntu loading screen with the circles under it and then the screen goes dark.  Dark as in I can't see anything but I can tell the back light is on.  I can press darker and brighter but it only varies the amount of darkness but nothing on the screen.  I believe it relates to this article: [http://ubuntuforums.org/showthread.php?t=1602710](http://ubuntuforums.org/showthread.php?t=1602710).  BUT, closing and re-opening the screen does not let me see it and unlike them, who had this problem from first install, I voluntarily, albeit unknowingly, chose to cause the problem =[.  

What I have tried to do:
-I have tried to access my linux partition using ex2read: [http://sourceforge.net/projects/ext2read/](http://sourceforge.net/projects/ext2read/) among another named something like ex2fsexplorer but neither worked.  This leads me to believe I somehow deleted/removed my linux partition but I am nowhere near sure.

-I don't currently have an external monitor and don't know if and when I can get one to see if it "just" the ATI graphics card.  

-I tried loading the usb distro to see if I can access my file to transfer it to Windows but again, can't find the partition.  I also used this distro to insert the vgaswitcheroo code from the above mentioned forum/post to no avail.

Any help is appreciated.  I am fairly new to Ubuntu (i.e. I have used it before to do some coding with gedit and gcc from .  terminal) so I lack experience and knowledge... please forgive me.  Let me know if there is anymore information necessary. Thanks!!!

---

### Post by electricj on 2011-02-03
Can you use Control+F1 to get to a console?  You might have to use Control+fn+F1 on this laptop.

---

### Post by yelojakit on 2011-02-03
I'm not completely sure what a console is but after trying to press the buttons, nothing happened. 

Something I did not mention is that, I am able to access GRUB.  Don't know if this matters but just in case.

And thanks for the reply, I thought no one was going to help.

---

### Post by electricj on 2011-02-03
Hmm, well I think that if you get the ubuntu loading screen then your partition is where it is supposed to be.  Once I pooched my linux partition then could only a message to the effect of "operating system not found" after selecting it in GRUB.

Is there a grub menu option for a safe mode that you can take?  I had some similar problems that needed me to keep the modules for the graphics card from being loaded, else the backlight would shut off and not turn back on.


If your brighter/dimmer buttons are working, I think thats a good sign.  IIRC on mine those signals are processed as acpi events, so that would mean stuff is running on yours.  If they were working before, do the keyboard LED's work (capslock, mute, wireless)?  Any sounds from the speakers (I think there usually is a kinda drum noise that happens when an ubuntu system starts up... Thats usually the first thing I turn off though, so I may be mistaken.

If you load the live usb and look at your partitions in gparted, does it provide any insight?

---

### Post by yelojakit on 2011-02-05
> **electricj said:**
> Hmm, well I think that if you get the ubuntu loading screen then your partition is where it is supposed to be.  Once I pooched my linux partition then could only a message to the effect of "operating system not found" after selecting it in GRUB.

Is there a grub menu option for a safe mode that you can take?  I had some similar problems that needed me to keep the modules for the graphics card from being loaded, else the backlight would shut off and not turn back on.


If your brighter/dimmer buttons are working, I think thats a good sign.  IIRC on mine those signals are processed as acpi events, so that would mean stuff is running on yours.  If they were working before, do the keyboard LED's work (capslock, mute, wireless)?  Any sounds from the speakers (I think there usually is a kinda drum noise that happens when an ubuntu system starts up... Thats usually the first thing I turn off though, so I may be mistaken.

If you load the live usb and look at your partitions in gparted, does it provide any insight?

Yeah, there is a safe mode to boot into, but it doesn't help anything.  Yeah the drum noise doesn't come at all.  But, when I force close (by pressing the power button) the ubuntu icon with the five circles under it does reappear briefly.  Running the live usb DOES have the drum noise.

No, not really because in all of those partitions I can't find my ubuntu one.  Plus, they're all named sdaX, where X is some number and unfortunately I don't know who that belongs to.

---

### Post by electricj on 2011-02-06
The sdaX thing is important; sda1 would be the label of the first partition on the first hard drive.  Have you been actually mounting the partitions to see what is on them, or just having a quick look for a familiar looking label?

On this laptop you might have a bunch more partitions than you really expect, since HP put a bunch of crap on there for recovery etc.  On my dual boot setup I have sda1 - sda5.  Windows lives on sda2 and my linux system is on sda5, but your setup will probably be different.

So if you can see a bunch of sdaX partitions, try mounting them all to see which one you linux system is on (or I guess we could also check to see which one GRUB is using to boot it).  If that works out then it should be no biggie to get you file and/or fix your graphics

---

### Post by yelojakit on 2012-02-19
I got too busy to ever fix this. I apologize and thank electricj for his efforts.

A year later, I went to a Linux Build event and got Ubuntu 11.10, which had fixed all the touchscreen/ati display problems (well, most of them).

---

