---
title: "Serial ATA Drive"
date: 2005-04-06
forum: Hardware &amp; Laptops
---

### Post by MrParker on 2005-04-06
Hey, you'll have to mind my ignorance as I'm new to linux....

I just got ubuntu (I love it, I tried mandrake prior to it, breath of fresh air in my opinion)... I've managed to get cedega up and running well, as well as many games.

My problem: I have a SATA hard drive as well as the IDE one I used for install. It is formatted using NTFS. 
I see my VIA chipset SATA drivers in devices, as well I see the harddrive in the collapsable menu. It says the device is at /sys/block/sda... What I need to know is how to mount it so I can access the files on it. 

I'm sorry if this is a stupid question, but I'm really new at this stuff :)
Thanks,
MrParker

---

### Post by soul_rebel on 2005-04-07
try 
mount /dev/sda1 /mnt/an_empty_dir

---

### Post by blendo on 2005-04-11
My Sata drive is not recogniced during Installation with 64 BIT CDROM Image?

someone any Ideas ?

 [-o<

---

### Post by clientserver on 2005-04-11
Try the workarounds listed in
[Bug 1440](https://bugzilla.ubuntu.com/show_bug.cgi?id=1440) 
[KernelTrap Report](http://kerneltrap.org/node/3971) 
and the previous forum threads
[Ubuntu Forum Thread 1](http://www.ubuntuforums.org/showthread.php?t=22542) 
[Ubuntu Forum Thread 2](http://www.ubuntuforums.org/showthread.php?t=18807) 
[Ubuntu Forum Thread 3](http://www.ubuntuforums.org/showthread.php?t=18808) 

If none of those help then the first thing to do is probably to continue to post here and hopefully someone will have ideas as to a better workaround / fix.

---

### Post by alastair on 2005-04-11
Look at your logs i.e.

/var/log/syslog

Look for lines related to IDE and disks - normal/warnings/errors etc. See what the kernel recognises at boot.

It might just be a BIOS problem (SATA "legacy"?).

---

### Post by blendo on 2005-04-12
Suse 9.2 Installs with no problems but it is slow

suse output on lsmod

-----------
sata_uli                8064  3
libata                 46856  1 sata_uli
sd_mod                 18072  4
scsi_mod              130432  5 sg,st,sr_mod,libata,sd_mod
------------

So I think there might be some problems with the controler ?

---

### Post by clientserver on 2005-04-12
blendo,
It probably isn't a hardware problem -- if the slowdown is with the CD then it could be that dma isn't enabled for the CD, if it is with the harddisks then your hdparm settings may be suboptimal.

If possible, post here the complete output of the 'dmesg' command after you go through the cd and hardware detection phases (or as far as you can get before the partitioning step) of the Ubuntu install.  You can switch to a terminal with Alt-F2 (and back to the installer with Alt-F1).
You might also want to compare that with the dmesg output from your Suse setup.

---

