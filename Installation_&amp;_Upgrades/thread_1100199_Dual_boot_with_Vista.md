---
title: "Dual boot with Vista"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by tjsanda on 2009-03-18
I am new to this so please forgive me.  I have 2 80gig Hdd's in Raid 0 configuration with Windows Vista installed.  Is it possible to add Ubuntu as a second operating system?

---

### Post by mdharp on 2009-03-19
Hi. I don't use Vista, but with Win XP, I have had good results with dual boot system, but no experience with RAID over 2 drives etc.
First : you will need to wipe the hard drive, & create partitions on your hard drive. This means you will probably need to format the hard drive & re install Windows on the first partition created. 
I usually create 3 partitions, & format the first two NTFS, install Windows on the first partition. eg; 250 GB HD = approx 3 x 80 GB partitions. Then "always" install Windows first.
The 3rd part of the hard drive needs to be left "raw" or "no partition". This is where Ubuntu installs. Make sure you have your internet connected when installing. As install progresses, choose the "use largest continuous free space" option to install on. It normally shows a screen asking if it should install eg; _ext3_ on 70GB partition, & then _swap_ on another 2 or 3 Gb partition . It is usually quite automatic from there on. Be sure to install Grub boot loader in Master Boot Record. That should be the last step.
Hope this helps. 
May be worth searching forum about installing on another 2nd hard drive to save wiping Vista install.
Good luck.

---

### Post by Mark Phelps on 2009-03-21
> **tjsanda said:**
> I am new to this so please forgive me.  I have 2 80gig Hdd's in Raid 0 configuration with Windows Vista installed.  Is it possible to add Ubuntu as a second operating system?

Since installing in RAID seems to involve "wiping" Vista, just be sure you have the capability to reinstall Vista with the full setup (files, apps, settings) that you have today and ensure that the activation is not removed -- which means you'll need a LOT more than just a DVD.

---

### Post by mdharp on 2009-03-22
It might be worth checking out GPart_ed partition editor. I have just succesfully added Ubuntu to 2 hard drives with Win XP already installed - no format or delete partitions required.
< _Please note_ > : _I am not sure if this works with RAID config_, so be sure to research this option. Otherwise - fantastic !!
Read instructions - & be sure to grab the recommended JkDefrag portable app to defragment & optimise your Vista partition to the beginning of hard drive, before re sizing partition.
Good luck !

---

### Post by tjsanda on 2009-04-23
Well, I never could get 8.10 installed on my raid.  Apparently, Dmraid did not support my controller.  

9.04 on the other hand supports it and is installed and working beautifully.

---

### Post by Sef on 2009-04-23
If you dual boot with Vista, you need to use the Vista partitioner to shrink the Vista partition.

---

### Post by tjsanda on 2009-04-28
Now that I have everything set up and working properly, I don't even log in to Windows any more.  Sure, when I want to play some COD 4 I'll have to, but that's it.  As soon as games start supporting Linux, it will be gone!

---

### Post by ohnoezitasploded on 2009-05-07
I have a Vista 64-bit install on a software RAID-0 array, like you.  I've shrunk the partition using the Vista utility, and I'd like to install 9.04 AMDx64 on the free space as a dual-boot setup.

I followed the instructions on the fakeraidhowto until I started getting cryptic failure messages, which was on instruction l-ii.  After that, I did the best I could to figure out what to punch in.

So Ubuntu installed all right, but now when I select the Ubuntu option I created at startup, I get dumped out to a grub> prompt.

What am I missing to complete my installation?  If you have a helpful link that explains what all this bootloader and chainloader +1 crap is, that would also be appreciated.

Thanks!

---

### Post by ohnoezitasploded on 2009-05-08
After two days and at least five delete-partition-and-reinstall attempts, I finally have a working dual-boot.  Here's where I ran into problems, and how I solved them:

start here:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

When the instructions start giving you weird errors, create the directories manually (sudo mkdir /target, e.g.), then re-run the commands, sort of like the guy at the bottom of page 3 of this post:
[http://ubuntuforums.org/showthread.php?t=630644&page=3](http://ubuntuforums.org/showthread.php?t=630644&page=3)

to get the dual-boot working, EasyBCD 1.7.2 does NOT work.  Install the EasyBCD 2.0 beta instead, then follow the directions here:
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4)

Gawd, what a nightmare.  Really, software RAID needs to be supported by the Ubuntu installer automatically-- it's not an uncommon configuration.

---

