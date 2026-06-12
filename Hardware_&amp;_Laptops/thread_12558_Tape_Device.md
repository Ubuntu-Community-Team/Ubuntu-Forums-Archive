---
title: "Tape Device"
date: 2005-01-25
forum: Hardware &amp; Laptops
---

### Post by julien_g on 2005-01-25
Hi,

I recently tried to install my Seagate ST8000A ATAPI tape device on ubuntu.
I tried adding *alias /dev/ht0 ide-tape* to /etc/modutils/aliases and run update-modules afterwards, which went well. But when I reboot my system and *lsmod | grep ide*, there is no ide-tape module running.

*modprobe ide-tape* while the system is already running works, though. Yet it seems to be too late for the system to map /dev/hdd (this is where the device is connected) to /dev/ht0 so that none of both is available.

Any suggestions?
Thanks in advance

---

### Post by julien_g on 2005-02-01
hdd: Seagate STT8000A, ATAPI TAPE drive
hdd: IRQ probe failed (0xffffbff8)

(from /var/log/dmesg)

yet it doesnt map it, /dev/hdd doesnt work

---

### Post by RichP on 2005-02-10
Did you try using makedev?

I haven't done this but I have been looking into it and I think you have to do something like:

cd /dev
./MAKEDEV ht


check out **man makedev ** for more info

Good luck!

---

### Post by julien_g on 2005-02-22
[QUOTE=RichP]Did you try using makedev?
cd /dev
./MAKEDEV ht
[/QUOTE]

Both ./MAKEDEV ht0 and ./MAKEDEV hdc (the streamer resides at /dev/hdc now) run without complaining, but the devices / files aren't actually being created.
Also, ./MAKEDEV local whatever complains about ./MAKEDEV.local being inexistent.

---

### Post by fleece on 2005-05-06
I have the same problem with the same tape drive.  I found this link that seems to offer insight.  I have not tried it yet, but I will shortly, and I will post my results.

[http://baheyeldin.com/linux/using-tape-backup-on-linux-for-a-home-network.html](http://baheyeldin.com/linux/using-tape-backup-on-linux-for-a-home-network.html)

---

### Post by fleece on 2005-05-09
Sorry - I don't have the same drive.  I have a Seagate STT20000A IDE ATAPI tape drive, but the instructions at the site in my previous post worked fine.  I did not create any devices by hand, create any mount points by hand, or actually mount anything.  The hd**x**=ide-scsi kernel option seems to make it all work (where **x** is the letter of the IDE position for that drive).

/fleece

---

### Post by fromgi on 2007-06-15
> **fleece said:**
> Sorry - I don't have the same drive.  I have a Seagate STT20000A IDE ATAPI tape drive, but the instructions at the site in my previous post worked fine.  I did not create any devices by hand, create any mount points by hand, or actually mount anything.  The hd**x**=ide-scsi kernel option seems to make it all work (where **x** is the letter of the IDE position for that drive).

/fleece

Fleece, I know it has been a few years, but can you please help me?  I too have a Seagate STT2000A, but not able to find the correct lilo or grub configuration files.

I did enter "hd0=ide-scsi" in the file lifo.conf which is located in /use/share/doc/memtest86+samples and rebooted.  This location doesn't seem correct, but it's the only place I found any kind of configuration file. 

I tried the commands, provided in the above link, but all responses are: "Input /Output error".

Can you PLEASE offer your guidance?

Thanks,
Larry

---

### Post by fleece on 2007-06-15
Hey Larry - anything that used to be in my brain on this topic has long been flushed.  However, just googling the terms "ide-scsi kernel grub" leads me to this page 
[http://www.justlinux.com/nhf/Compiling_Kernels/20_Steps_to_a_New_Kernel_with_Grub.html](http://www.justlinux.com/nhf/Compiling_Kernels/20_Steps_to_a_New_Kernel_with_Grub.html)
Which shows examples of a grub config file that includes passing the kernel the option to load the ide-scsi emulation for a specific drive.

I think your challenge may be that you are editing a sample config file and not the "real" one.  Referring to [http://ubuntuforums.org/showthread.php?p=1508435](http://ubuntuforums.org/showthread.php?p=1508435) makes me think you should alter the file /boot/grub/menu.lst

Note: I haven't done any of this...I'm just a person googling for info so YMMV.

---

### Post by fromgi on 2007-06-17
Thank you for the speedy replay!  We truly appreciate the time and efforts you have shown.

I'm a teacher in a High School and was asked by many of our computer students to allow them to install Ubuntu.  We decided to give it a try.  We finally decided to install Ubuntu on two computers.   These two computers are about three years old and contain both tape and floppy drives. 

In addition to other tasks, one assignment was to get all these devices working.  I had 7 of my best students try to get them to work.   After three weeks (summer vacation began yesterday), they could not get the tape drive to work.  When booting to XP, the drive worked fine.

My students followed Ubuntu's instructions (Official Ubuntu documentation website) , but was still not able to watch all videos and encountered syntax errors within it as well.  They were not impressed with the Gaim Messenger and still bothered by some videos not able to play.  We all know how important videos and messengers are to teenagers!

The bottom line.  After nearly a month, they thanked me for allowing them to try Ubuntu; however, decided to stay with XP.

Thanks again,
Larry

---

