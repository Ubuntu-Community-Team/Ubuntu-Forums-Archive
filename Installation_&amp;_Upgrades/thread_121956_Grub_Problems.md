---
title: "Grub Problems"
date: 2006-01-26
forum: Installation &amp; Upgrades
---

### Post by firekat on 2006-01-26
Greetings all!

I am attempting to install AMD64 Unbuntu on Athlon 64 3500 machine.  It is running a RAID 0 striped for XP.  For the Unbuntu installation I installed a 100G SATA drive (not in the raid array).  I tried doing a regular Unbuntu install.  I got to the point where is was doing a reboot and then it hung with a grub 21 error.  From what I understand grub was written to the MBR of one of the drives in the array (XP was no longer bootable after Unbuntu installation).  I reset the array (through it's BIOS) and did a restore on the original system.

What I would like to do, not that I know that it would work is have grub installed on the SATA drive that I install Unbuntu on.  My reasoning here is that I can select through the motherboard BIOS the boot order of the specific installed discs/arrays.  I can even "disable" any of them to prevent them from booting.

Can anyone shed any light on how to do this.  I have tried installation a number of times and have not gotten anywhere on this issue.  I do not know how I can keep the installation from installing grub or determining where it will be installed or if it will work for that matter afterwards though I do remain optomistic.

Thanks in advance!

---

### Post by BenTyreman on 2006-01-26
Try doing an expert installation. It should allow you to choose where to put GRUB, or at the very least to not install GRUB at all. You could then install GRUB manually.

---

### Post by firekat on 2006-01-26
I am currently trying the "expert" installation method.  Right now I have been having problems with grub being written to the MBR of the third drive as was defined in the partitioning dialog.

I inputted "dev/sdc" into the grub interface and it has come back as an installation failure.  I even tried doing it to the floppy.  I just stuffed one in and figured that it would be appropriately formatted and written.  When I tried re-starting it came up and said that it was unreadable or something to that effect.

Still trying and burning up too much time inside during a beautiful morning!

---

### Post by MJN on 2006-01-26
[quote=firekat] I inputted "dev/sdc" into the grub interface ...[/quote]

I trust that was actually    **/dev/sdc**     ?

Mathew

---

### Post by BenTyreman on 2006-01-26
GRUB doesn't work of names like /dev/sdc. You would need to use (hd2) to get /dev/sdc. Unless you are running the grub-setup <drive> from the command line, in which case it is the standard naming scheme.

If GRUB setup still fails during the installation, ctrl+f2 to a different console and run grub-setup /dev/sdc. It might give a more verbose error message.

---

### Post by firekat on 2006-01-26
Well yes dummy me, went back and put in the forgotten "/" and it loaded.  Now grub comes up and gives me "ERROR 21: Selected disk does not exist, Press any key to continue..."

It comes up with a selection of different operating modes (AMD 64 stuff) and when I try any of them it comes back with the same error message.

So close yet so far!

---

### Post by firekat on 2006-01-26
Ok, I guess the thing to do now is figure out what kind of editing I need to do to get this thing running.

I don't fully understand all the machinations here but I would assume that changing some of the parameters here would help.

I tried editing the root from (hd2,0)if I remember correctly, to (sdc,0) that brought up this message: "Error 23: Error while parsing number"

So any ideas?   Thanks!

---

### Post by Topsiho on 2006-01-26
Hello firekat,

Googling with Grub error 21 took met to the next answer to the same problem:


===========
I guess you've already seen this from the Grub manual:

21 : Selected disk does not exist
     This error is returned if the device part of a device- or full file
     name refers to a disk or BIOS device that is not present or not
     recognized by the BIOS in the system. 


The thing is, Linux itself will see the drive even if it's not enabled
in the BIOS setup, but GRUB won't because it depends on the BIOS to do
that. That explains why you can see it from Knoppix, and why you could 
install Debian there to begin with.

Seems pretty clear that the drive is there and working as far as Linux
is concerned. Why the BIOS won't recognize it is the question. Does it
get detected if you (temporarily) move it to another position like the
secondary slave?
===========


I guess this is it, you have to tell your BIOS about the drive which it doesn't see by itself.

Good luck,

Topsiho

(the best advice here is to use Google :)  )

---

### Post by BenTyreman on 2006-01-26
(hd2,0) should be correct. It's certainly better than using sdc.

Could you post your /boot/grub/menu.lst and fdisk -l?

Have you tried (hd2,1)?

---

### Post by firekat on 2006-01-26
Just tried the (hd2,1), comes back with Error 21: Selected disk does not exist.

How do I get to /boot/grub/menu.lst and fdisk -l stuff?  

Right now I am only in grub that is as far as I can get.

thanks

---

### Post by lha on 2006-01-26
[QUOTE=firekat]Ok, I guess the thing to do now is figure out what kind of editing I need to do to get this thing running.

I don't fully understand all the machinations here but I would assume that changing some of the parameters here would help.

I tried editing the root from (hd2,0)if I remember correctly, to (sdc,0) that brought up this message: "Error 23: Error while parsing number"

So any ideas?   Thanks![/QUOTE]

Drive numbers (as grub sees them) depend on bios boot order. If you have set bios to boot from sdc, grub sees this drive as (hd0). Try if it works. (I mean you should try (hd0,0) instead of (hd2,0).) If it does, drop a note here, because your menu.lst and devices.map need to be fixed.

---

### Post by firekat on 2006-01-26
Ok, I changed the drive number to (hd0,0) and it started loading!  Then it seemed that things just wouldn't work after that.  Ubuntu would show that updates were available, type in a password - nothing, click on the icon again - nothing.  I tried re-booting and found that the editing to the drive number line in grub was not saved and I have to re-edit it for it to start again.

Right now what I am attempting to do is to reload the whole magilla with the array in the bios disabled (for boot purposes) see how the auto loading of ubuntu works out and if it dumps grub into the MBR of the Raid array.

Well see.

---

### Post by firekat on 2006-01-26
Well I seem to be getting the system to work.  The auto loading worked better than the "expert" mode and I could start working on the system and do some updates.

Still not able to get grub to save the edits, how is that done?  This is to say nothing about not being able to "find" the XP installation, albeit I have that non-bootable right now.  How would I edit these functions?

Ubuntu seems pretty nice though I am thrashing around trying to set up the video resolution and I am having nightmares with the sound card.  Going through all the information is quite time consuming.  The system itself does seem promising - once I can get it set up.

I have done a bit of thrashing about with Linux in the past before so the little bit that I learned back then is coming back - I just didn't know that much even then!

---

### Post by lha on 2006-01-26
[QUOTE=firekat]Well I seem to be getting the system to work.  The auto loading worked better than the "expert" mode and I could start working on the system and do some updates.

Still not able to get grub to save the edits, how is that done?  This is to say nothing about not being able to "find" the XP installation, albeit I have that non-bootable right now.  How would I edit these functions?

Ubuntu seems pretty nice though I am thrashing around trying to set up the video resolution and I am having nightmares with the sound card.  Going through all the information is quite time consuming.  The system itself does seem promising - once I can get it set up.

I have done a bit of thrashing about with Linux in the past before so the little bit that I learned back then is coming back - I just didn't know that much even then![/QUOTE]

Open a terminal and type
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
``` to make a backup. Then use
```
sudo gedit menu.lst
``` to edit the file which contains grub options. You'll need to replace references to hd2 with hd0, including the commented line '#groot (hd2,0)'.

What kind of problems are you having with booting windows?

---

### Post by BenTyreman on 2006-01-26
The GRUB settings are stored in /boot/grub/menu.lst, although I am sure there is a GUI front-end out there somewhere. You will need to modify this file to make the changes permanent.

The XP installation will not be picked up. Linux lacks the ability to read the hard disks as a RAID array. It sees them as two separate drives. Because they are RAIDed, it looks to linux like they have corrupted partitions on them.

When I was dual-booting, I copied the MBR off the linux installation and transferred it to the XP installation, adding it as another entry in the boot.ini file. There are several tutorials explaining this procedure.

The most difficult things I had to do was to get the sound and graphics working right. I have found that running dpkg-reconfigure xserver-xorg will usually get the graphics working better than is provided by the standard installation. If you have an nvidia or an ATI card, you will benefit from installing the updated drivers.

Eventually, I completely removed the XP installation, removed the RAID array, and used linux software RAID to recreate the array. If you want, XP can be reinstalled on the stand-alone hard drive. This will allow for easier GRUB configuration, with no messing about copying the MBR over to XP.

---

### Post by firekat on 2006-01-27
Thanks for the info.  I will be checking the grub stuff in a bit.

I have been wrestling with getting Ubuntu configured - it's been very very time consuming.  I am no computer expert so it takes time.  It has been 3+ strikes for me with mouse/graphire pad, video, sound and grub issues.  I was just about to pull the plug on the whole deal.  With all your help I have partially fixed the grub issue and I was able to get the mouse/graphire problems sorted out.  That one was a deal killer, ever try using a mouse wheel running backwards?  Also the mouse was in "absolute" mode making desktop navigation a real big pain in the a**!

Have to get back to work on other things - including getting XP re-running and configured with some apps that I require and are currently working (sound apps, graphics apps)  I do dread going back to XP as all the firewalls, adaware, spybot, viruses, spyware, and system just getting clogged up - and this seems to happen more and more quickly is just driving me nuts!

Hopefully things will work out with this Ubuntu though there will always be some stuff I have to run in XP as I have yet to see replacements in the Linux world and some of the stuff I do requires some oomph!  With Ubuntu I should at least be able to take advantage of my AMD 64 architecture - hopefully.

Thanks!

---

### Post by baytuni on 2006-01-27
i have a similar problem. I have ubuntu installed on my sata drive and windows on ide and successfully configured grub to boot up the ubuntu, ,however couldn't manage to add the windows boot in the grub menu. I took into account what lha said > Drive numbers (as grub sees them) depend on bios boot order. If you have set bios to boot from sdc, grub sees this drive as (hd0). Try if it works. (I mean you should try (hd0,0) instead of (hd2,0).) If it does, drop a note here, because your menu.lst and devices.map need to be fixed. here is my menu.lst
```
title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda8 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin  
boot

title windows
root (hd1,0)
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```
but grub insists on not loading windows saying unknown file system. Thanks for helping out.

---

### Post by lha on 2006-01-27
[QUOTE=baytuni]i have a similar problem. I have ubuntu installed on my sata drive and windows on ide and successfully configured grub to boot up the ubuntu, ,however couldn't manage to add the windows boot in the grub menu. I took into account what lha said  here is my menu.lst
```
title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda8 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin  
boot

title windows
root (hd1,0)
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```
but grub insists on not loading windows saying unknown file system. Thanks for helping out.[/QUOTE]

This should do the trick:
```
title windows
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

Please, put those lines *under*
```
### END DEBIAN AUTOMAGIC KERNELS LIST
``` or they will be removed when you upgrade kernel.

Windows gets pissed off if it isn't on hd(0). That 'map' thingy tricks it and lets you to have Windows on any hard drive.

---

### Post by baytuni on 2006-01-27
yeeha. Thank you so much. It worked pretty well.Three more questions. It waits 3 sec. to boot and expects me to press esc to enter the menu. Can it enter directly.How can change the default os. Finally a question from newbies talk [http://www.ubuntuforums.org/showthread.php?t=122366](http://www.ubuntuforums.org/showthread.php?t=122366)

---

### Post by lha on 2006-01-27
[QUOTE=baytuni]yeeha. Thank you so much. It worked pretty well.Three more questions. It waits 3 sec. to boot and expects me to press esc to enter the menu. Can it enter directly.How can change the default os. Finally a question from newbies talk [http://www.ubuntuforums.org/showthread.php?t=122366](http://www.ubuntuforums.org/showthread.php?t=122366)[/QUOTE]

Open menu.lst and find line
```
hiddenmenu
``` Comment it out, like this:
```
#hiddenmenu
```

Change
```
default         0
```
to something else, like
```
default         4
```

---

