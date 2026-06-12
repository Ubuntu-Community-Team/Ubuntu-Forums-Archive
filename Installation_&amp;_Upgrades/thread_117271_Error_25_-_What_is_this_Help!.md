---
title: "Error 25 - What is this? Help!"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by John E Davies on 2006-01-14
Hi;

This  is my first post - I am a total newbie at Linux, and while I am reasonably competent with Windows, I don't know anything about programming.

I am part way through an install of Ubuntu 5.10 onto my Win XP machine. I want to dual boot with Win. Everything was going fine until the first reboot. I removed the CD and rebooted, and the process hung at the "GRUB loading Stage 1.5" step. The hard drive is active continually, but nothing happens for 2 minutes and I then get an "Error 25" message, and then nothing more. I rebooted with no change in symptoms. It has been 30 miutes and the system is still hung.

What is Error 25, and how do I correct this boot problem?

I can't get into Windows on my PC, so I have to access this forum via my wife's laptop. I don't know how to access the C Drive of my main computer to check error logs.

Basic info:
Pentium 2.4, 512 MB RAM, 3 hard drives (Linux PARTLY installed onto the 2nd Master, 80 GB) Windows XP Home Edition with all updates.

HELP! I can provide reasonably detailed setup info on the system if that is necessary. How can I get past this error message? 

Thanks very much.

John

---

### Post by Kipper on 2006-01-14
John,

You may have already figured out that the "Error 25" is produced by the GRUB bootloader which has been installed in your hard drive's MBR as part of the Ubuntu install. 

If you actually got to the part of the Ubuntu install where it asks you to remove the Ubuntu Install CD from your drive then you might get your system to boot correctly and complete the install by re-installing GRUB. 

Turn you rmachine off. Turn it back on with the install CD still in your cd-rom. Your are going to use the "rescue" mode to re-install GRUB. The instructions are:
  
Boot with your Ubuntu installation CD
On the  boot:  prompt, type  rescue  and hit enter
Follow the instructions on the screen
When the computer is ready, assuming that  /dev/hda  is where your  /boot  is located, type:  **grub-install /dev/hda**

As you have multiple drives in your machine, as long as the hard drive you installed on was the first drive in the boot order for your BIOS, then /dev/hda is correct. If this works, on re-booting your machine you should complete the install.

Alternatively, you can just install again, but when you get to the "partitioning" part you'll problay have to delete the partition(S) created for Ubuntu first time around so you can resuse that space. See here for a guide about dual booting : [http://www.users.bigpond.net.au/hermanzone/](http://www.users.bigpond.net.au/hermanzone/)

As a last resort, to restore booting to WinXP you'll have to go through the Windows rescue process to restore the MBR (/fixmbr), which will remove GRUB.

---

### Post by SilentCacophony on 2006-01-14
Good suggestions above. I'll add a couple of thoughts to that.

I believe I remember an outdated bios being another possible culprit for that error, in that the motherboard bios cannot deal with extended partitions on more modern (large) harddisks. If so, the bios can usually be updated to handle it (not for the faint of heart, or uninformed, though.)

Since grub will typically store the menu.lst file on the ubuntu partition if you choose to install it to the MBR, another thing one can try if experiencing problems with booting from HD is to do the "rescue" operation as explained in the above post, but to choose to install grub to a floppy (/dev/fd0) instead of the MBR (/dev/hda). This should give a relatively fool-proof way to boot into the windows partition even if there are problems with the linux partition and/or it's grub menu.lst file. I make a floppy backup after doing the normal MBR install, myself.

---

### Post by John E Davies on 2006-01-15
Thanks to  you both. I wish I had stuck around longer yesterday to read your helpful comments. I did get my Windows system restored, but it was a long ordeal. Mainly because of lack of knowledge, I ended up reformatting and reinstalling Windows XP, then using my Imaging software to restore the drive data. I haven't gotten the Linux boot situation figured out yet, but I will try some stuff with the info you provided me.

I do have a large number 1 hard drive - it is a brand new 200 GB Ultra/ATA/133. It may be that my BIOS is the issue, since I had to format the big hard drive from within WIndows XP with the latest Service Pack, otherwise I would only have had 137 GB. I guess this shows a VERY good reason to not install new hardware and a new operating system virtually simultaneously. (Though the new hard drive was working dandy before I started the Linux install.) My plan was to retire my "old" 80 GB C-drive and use it to dual boot into Linux.

I will check out the BIOS issue first, to see if I can get that resolved. I have done BIOS updates before, and I am willing to do so again.

My current Award BIOS Boot options do NOT include a second hard drive. They are currently set in this order:

DVD/ROM
Floppy
IDE Hard Drive (200 GB with two 100 GB partitons)
Other Boot Device - DISABLED 
            (options are SCSI Boot Device and INT18 Network Device)

Do I definitely need to have a second hard drive option listed in my BIOS for Linux to dual boot using GRUB?

After that I will try messing with GRUB some more. I really would rather boot from a floppy or CD/R at this point, for safety's sake.

Last question: is there a site that lists ALL the GRUB error messages? I found one page, but Error 25 was not shown.

I really think there should be more documentation and warning messages about dual booting with GRUB, with some suggestions for avoiding or repairing the situation I ran into. The consequences are too severe to not have the info there and readily available to the novice user. When your computer is completely dead, you are out of luck unless you have another computer avaialable with an Internet connection.

Thanks again, and if I have more problems I will be sure to check back here.

Also, many thanks to my young nephew David Smith, aka "catfish.man", who is a very knowledgeable and active member of the Linux community. I am not sure if he is a member here.... he should be. Is there a Member List link somewhere? He helped me a lot to resolve my drive problem.

John Davies

---

### Post by Herman on 2006-01-15
Hi, John, here's a link to the GRUB manual, you can look up error codes in that, it is very helpful. 
[http://www.gnu.org/software/grub/manual/grub.html]("http://www.gnu.org/software/grub/manual/grub.html")
There is also another bootloader, GAG, that you can put on a floppy disk or a CD to use to boot Windows with if you get stuck when installing GRUB.
[http://gag.sourceforge.net/]("http://gag.sourceforge.net/")
I find GAG very handy at times myself, I have it installed now to disk in one computer now that I change the partitioning around in a lot.
I only have a little experience with single hard disk machines myself, and a healthy curiousity, but no formal training.
You are right, we do need more documentation. It is hard to decide how many warning messages we need and still invite people to go ahead and install. 
I think knowledge is the key, if we can supply the information for how to go ahead and do things and how to avoid problems or if not, how to cope when things don't go to plan things will be fine. There are already plenty of good manuals written, but they do tend to be rather 'dry' reading. It's only because they tend to be a little brief. There is room for people to read the manuals and re-write the same information in more digestable wording, and maybe some illustrations. That will make the information more accessable to most people.
(Herman):D

---

### Post by lha on 2006-01-16
[QUOTE=John E Davies]My plan was to retire my "old" 80 GB C-drive and use it to dual boot into Linux.

I will check out the BIOS issue first, to see if I can get that resolved. I have done BIOS updates before, and I am willing to do so again.

My current Award BIOS Boot options do NOT include a second hard drive. They are currently set in this order:

DVD/ROM
Floppy
IDE Hard Drive (200 GB with two 100 GB partitons)
Other Boot Device - DISABLED 
            (options are SCSI Boot Device and INT18 Network Device)

Do I definitely need to have a second hard drive option listed in my BIOS for Linux to dual boot using GRUB?

After that I will try messing with GRUB some more. I really would rather boot from a floppy or CD/R at this point, for safety's sake.

Last question: is there a site that lists ALL the GRUB error messages? I found one page, but Error 25 was not shown.[/QUOTE]

In my opinion, a dedicated drive for Ubuntu makes life easier. A good idea.

Updating BIOS will hardly do any good unless your computer is old. I have ~4 years old motherboard and it works fine and dandy with my 250GB drive. (With Linux, not with Windows.) Try if Ubuntu install cd partitioner sees your bigger drive properly and then decide if you need to do something with that BIOS.

No, you don't need the option to boot from secondary drive. This is a job for grub.


By far the easiest method of dual booting is to make your 80GB drive primary master and set bios to boot from it by default. 200GB (Windows) drive can be in any other ide channel, eg. primary slave. Install Ubuntu and grub on 80GB drive. Ubuntu installer should automatically detect Windows on the other drive and add appropriate lines to /boot/grub/menu.lst. You might need to add lines
```
map (hd0 hd1)
map (hd1 hd0)

```
to menu.lst, just below "title Windows XP". Your 200GB drive will stay intact. You can even remove 200 GB drive and install Ubuntu with only 80GB drive plugged in if you are paranoid. In that case you'll need to edit menu.lst afterwards to make grub show an option to boot into Windows.

If something goes wrong and you are not able to dual boot, just swap the places of your hds making 200 GB drive primary master and Windows boots up.

---

### Post by TeyNur on 2006-07-28
Sigh.

I've got this problem and will have to find time to work on this weekend but I've got a slightly different idea and need feedback to tell me whether or not it will work.

Like John, I have a three (3) drive system -- two IDE 30's running Win XP.  I just obtained a nice SATA 320 and had hoped (still do) to make it my Ubuntu system.

My BIOS will allow me to specify what device to boot from.  It was my hope that I could install Ubuntu solely on the 320 and then using the BIOS menu boot from whichever drive I wanted.  Dang!  That didn't quite work as planned.

But I think it still might be possible to do so.  Here's what I proposed and what I need feedback on.

I'm going to diconnect the SATA from the system until I can get my Windows machine restored using the instructions here. (Thanks)

I'm thinking if I (temporarily) disconnect my two IDE drives from my system that I should be able to install Ubuntu to the SATA completely.  If I then reconnect all three drives, would I then be able to use the BIOS menu to choose the boot device?  I'm not concerned about cross dive visibility but at the same time, I don't want to destablize my system... (Oh wait... I aldeady did that)  Well, let's just say I don't mind having to completely different systems running that aren't aware of each other.  They don't need to be.

The question is, will it work?  Is it advisable?

---

### Post by Good Ol' Ramos on 2007-02-07
I would like to add to this debachle...

I am having this error, but I had already installed Ubuntu a long time ago (I don't know, 2 months?) I installed it, played with it, and switched back to Windows because I suddenly became addicted to Call of Duty 2. Anyway, before I know it, Windows screws up BAD (a million issues all to themselves), so I decided to boot from HDD-01 (My Linux drive), and I now get this error? Any idea how to circumvent this without the disk? I lent it to a friend, and might not see them for a while. If not, I'll find a way to get it back, but until then... ?

---

### Post by confused57 on 2007-02-07
> **Good Ol' Ramos said:**
> I would like to add to this debachle...

I am having this error, but I had already installed Ubuntu a long time ago (I don't know, 2 months?) I installed it, played with it, and switched back to Windows because I suddenly became addicted to Call of Duty 2. Anyway, before I know it, Windows screws up BAD (a million issues all to themselves), so I decided to boot from HDD-01 (My Linux drive), and I now get this error? Any idea how to circumvent this without the disk? I lent it to a friend, and might not see them for a while. If not, I'll find a way to get it back, but until then... ?

Here's a description of grub error 25:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#25](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#25)

If you're getting a grub menu booting to your Ubuntu drive, you can try highlighting the Ubuntu entry, press "e" for edit, then change root (hd1,0) to root (hd0,0), & press "b" to boot.  
This change is temporary, but if it works, you can make it permanent in your /boot/grub/menu.lst.  Worth a try.

You might also want to download & burn a copy of the Super Grub Disk(approx 500 kb):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

It's an excellent utility to boot Ubuntu or Windows, restore mbr(grub or Windows)

---

### Post by Good Ol' Ramos on 2007-02-07
Once I'm done running a scan on my desktop, I'll give it a shot. Thanks for the help!

---

