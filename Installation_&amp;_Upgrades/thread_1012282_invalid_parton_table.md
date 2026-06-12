---
title: "invalid parton table"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by NuWeb on 2008-12-15
I was [unable to install Ubuntu](http://ubuntuforums.org/showthread.php?t=1011190) on my laptop, so i used a different computer.

... What I Have Done ...
I removed hardrive from laptop and attached it via USB to Computer.
I formatted and created new partion on hardrive.
I then installed Ubuntu
I then put the hardrive back into laptop.

Now i have "invalid partion table", how do I make it boot into ubuntu? 
I have window vista restore cd, if I can do it with that?
i dont have vista or any other os installed. I just want ubuntu!


Id love some help, It stopped been fun 24 hours ago. lol

Thanks In Advance.

---

### Post by logos34 on 2008-12-15
you need to fix the partition table with testdisk.  


Instructions here:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Disk_selection](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Disk_selection)

Boot the ubuntu live cd and do:

system>admin>software sources>enable universe repository

sudo apt-get install testdisk

sudo testdisk

---

### Post by caljohnsmith on 2008-12-15
Did you get a Grub error 5, which is "Partition table invalid or corrupt"? How about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo sfdisk -l
sudo fdisk -lu
sudo parted /dev/sda print
```

---

### Post by NuWeb on 2008-12-15
Thanks for the help, I am unable to boot into LiveCD because of [THIS](http://ubuntuforums.org/showthread.php?t=1011190)] hardware problems i guess.

Im trying to create a bootable USB, but having to compile that in windows. So fingers crossed.

---

### Post by wpshooter on 2008-12-15
Have you tried WIPING the hard drive using [www.killdisk.com](www.killdisk.com) ?

And then try installing Ubuntu from the ALTERNATE (text based) CD version.

Good luck.

---

### Post by NuWeb on 2008-12-16
Thanks for the lnk wpshooter, killdisk will erase all data on hardrive. Allowing me to reinstall ubuntu, except that if I run the Alternate Ubuntu Installation it says "Unable Detect and Mount CD-Rom" i have made a bootable ubuntu USB but laptop can not boot with usb :(

I dont think the computer wants to be on ubuntu.

---

### Post by logos34 on 2008-12-16
> **NuWeb said:**
> I was [unable to install Ubuntu](http://ubuntuforums.org/showthread.php?t=1011190) on my laptop...

...I am unable to boot into LiveCD because of THIS] hardware problems i guess.

just read that thread...ok, so you can't boot the live cd, hmm.  It'll be hard to do any diagnostics or run any commands at all without live session of some sort.  Also, smartboot won't work with USB, so that's not an option.

---

