---
title: "run ubuntu 8.10 desktop livecd without burning a CD and not using UNetBootin"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by centguy on 2009-01-10
I have checked a few relevant threads but they are not directly relevant or the methods they suggested are not suitable for me.

I am a regular linux user, so I don't think I will use UNetbootin technique.

I have downloaded ubuntu-8.10-desktop-i386.iso
and  I would like to boot up ubuntu iso from the hard drive.

I know how to copy the vmlinuz and initrd files to a place and then edit the menu.lst so that I can boot up, 
So far, two entries I have tried didn't work:

title Ubuntu Installer
        root (hd0,3)
        kernel /boot/vmlinuz-Ubuntu-8.10 vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
        initrd /boot/initrd-Ubuntu-8.10.gz


and another one:

title Ubuntu LiveCD @ sda7 (does not work !!)
       root (hd0,3)
       kernel /boot/vmlinuz-Ubuntu-8.10 file=/boot/ubuntu.seed root=/dev/sda7/casper
       initrd /boot/initrd-Ubuntu-8.10.gz

Can any body point out the correct stanza to use ?? Thanks a million!!


For the first one, it keeps saying "/dev/rd/0 does not exist! Dropping to a shell". The second one keep complain that it cannot find right root or something..

---

### Post by McFrostey on 2009-01-10
If youve already downloaded the ISO just shove a 80minute CDR into ur drive and burn it only takes 5miutes to burn... and then restart and boot from the CD Drive your making harder than what it really is...

---

### Post by boof1988 on 2009-01-10
Thanks for starting this thread...  I have been trying to figure out how to do this as well.

I have been using unetbootin and it seems to properly make a hard-disk-install-iso for Ubuntu 8.04.1 but it wont make the Ubuntu 8.10 hard-disk-install-iso properly (the startup menu is incorrect).

Thanks again for starting this thread and I look forward to an answer.

---

### Post by centguy on 2009-01-10
Well, there are many reasons why I want to do it the hard way and I might hope others will do the same too:

(1) If everybody can cut down the usage of the CD/DVD, the rate at which we use the world resources is reduced.

(2) It makes testing of new version of any linux distro easier before committing to it.

(3) At least I have encountered a case where installing a distro directly from an ISO resides on a harddrive is extremely painless compared to the conventional CD/DVD way (well, after many serious effort to find out why the DVD installation failure, I finally concluded that the linux kernel sort of confused by the  DVD reader, may be my DVD reader is not working properly, or for whatever reason..).

Could someone please point the most relevant places for me to try?

---

### Post by avtolle on 2009-01-10
Have you looked at [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)  ?

---

### Post by centguy on 2009-01-10
Latest update: My two posts in 

[http://ubuntuforums.org/showthread.php?t=457318](http://ubuntuforums.org/showthread.php?t=457318)

show that i have get it work using the fromiso trick.
Thanks guys!!

---

### Post by centguy on 2009-01-10
avtolle, that is exactly the one that I was looking for!! "unfortunately" I found a ubuntu thread that says there is a way to boot up directly from the iso, but then it takes a bit of an effort to patch the initrd file, which is non-official. I made it work after some concentrated effort.. Thanks again !!

---

### Post by centguy on 2009-01-11
boof1988, the thread that I pointed to confirms that fromiso trick work for intrepid. Also the web site avtolle pointed out should work. Of course, the initial setting is a preexisting working linux system.

I guess one day i will get serious with unetbootin since it seems it can run on a linux system and it is much easier to do without all the fuss of "mount -o loop ...", copy out vmlinuz and initrd, add a menu list entry, and having to play around with the magical boot parameters for boot=, root= stuff.

---

### Post by boof1988 on 2009-01-14
> **centguy said:**
> boof1988, the thread that I pointed to confirms that fromiso trick work for intrepid. Also the web site avtolle pointed out should work. Of course, the initial setting is a preexisting working linux system.

I guess one day i will get serious with unetbootin since it seems it can run on a linux system and it is much easier to do without all the fuss of "mount -o loop ...", copy out vmlinuz and initrd, add a menu list entry, and having to play around with the magical boot parameters for boot=, root= stuff.

Thanks centguy... I'll give these other methods a try.  Hopefully I'll learn some more about "mount -o loop" etc.  Have used it before and now it would be nice to understand what it means.

---

