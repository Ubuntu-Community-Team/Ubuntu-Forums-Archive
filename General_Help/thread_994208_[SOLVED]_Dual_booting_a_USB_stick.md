---
title: "[SOLVED] Dual booting a USB stick"
date: 2008-11-26
forum: General Help
---

### Post by Kevbert on 2008-11-26
USB sticks are getting bigger and bigger. Is it possible to dual boot a USB flash drive with two persistent operating systems ?  I have partitioned one with Xubuntu on one partition and puppy on another. How do I go about booting to either as there does not seem to be a menu.lst file and unetbootin does not see xubuntu ?
I know USB flash drives are cheap but want to find out how to do this.

---

### Post by opscure on 2008-11-26
Depends what boot manager you're using.  You don't have a menu.lst because you are not using grub.  You are probably using syslinux or lilo, in which case, you will want to edit the syslinux.cfg file or the /etc/lilo.conf file respectively.  You can find more information here:
[http://syslinux.zytor.com/wiki/index.php SYSLINUX#How_do_I_Configure_SYSLINUX.3F]("http://syslinux.zytor.com/wiki/index.php/SYSLINUX#How_do_I_Configure_SYSLINUX.3F")
and 
here:
[http://www.freeos.com/articles/2701/]("http://www.freeos.com/articles/2701/")

This is very possible as I have done it with four OS's on one flash drive, I used grub, but to each his own I suppose.

---

### Post by Kevbert on 2008-11-26
Thanks for the link opscure. I have syslinux.

---

### Post by Kevbert on 2008-11-27
I'm having a bit of a problem getting my head around this.
Both Xubuntu and Puppy use syslinux.cfg. If I add the Xubuntu sysinfo.cfg to the Puppy one I get Xubuntu showing up on the boot screen but it won't boot into Xubuntu (or anything) if I copy and paste the Xubuntu sysinfo.cfg. Here's what I have so far:

```
default vesamenu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit pmedia=cd

label ubnentry0
menu label Puppy
kernel /vmlinuz
append initrd=/initrd.gz pmedia=cd

label ubnentry1
menu label Xubuntu 8.10
root (0,1)
kernel ???
append initrd=/initrd.gz pmedia=cd
```

What do I use for kernel as there is no vmlinuz ? I've attached the sysinfo.cfg for Xubuntu.

---

### Post by opscure on 2008-12-03
The easiest way to accomplish what you are trying to do is to make 4 partitions on your thumb drive.
sda1 - boot partition - 50mb - boot flag
sda2 - xubuntu partition - whatever size - ext2
sda3 - puppy partition - whatever size - ext2 
sda4 - swap partition - 100mb 

Use the Xubuntu installer to install grub to the first partition.  Then follow the installation through and install xubuntu to the second partition.  Insert the puppy install cd and install to the third partition.  Then edit your /boot/grub/menu.lst file in your first partition to add puppy to it.  

This should be easier for you then messing around with syslinux.  

On the other hand, you can use the kernel from the xubuntu cd, the initrd, and the filesystem image. This should be copied over to your partition and added to sysinfo.cfg file.

---

### Post by Kevbert on 2008-12-03
Will that make the xubuntu install persistent? I've heard that if I use the pendrive as if it was a hard disk it would drastically reduce the life of it.  If it's persistent I would not need swap either.

---

### Post by opscure on 2008-12-03
The whole argument of persistence is still up in the air (imo).  Any newer drives say they will last about 10 years regardless of how many writes are preformed.  

This may or may not be the case, since I have not tested this for 10 years yet.  I have tested multiple OS's running on a thumbdrive for about 1.5 years without fail due to writes. If you plan on using this for a short period of time (ie until the next major/new/fun distro comes out) then I don't think you will have an issue using it like a HD.  

On the other hand if you want to have a live based system, that retains data through reboots then I would look towards using more of a memory based OS, like DSL.  With DSL the OS remains constant and you simply add extensions for improved functionality.  All files modified and saved will then be written one time on shutdown to the backup.tgz file automatically.   

This OS would save you the writes to the disk that you are concerned may hinder the life of the stick while still giving you the functionality you may want from linux.

Not too sure in your purpose/reasons for doing this, so I'm sorry if I'm not directing my answers in the right direction.

---

### Post by Kevbert on 2008-12-04
Thanks for all the help.
It's just for fun to see if it's possible. 
I'm also going to have a go at doing this with XP so that I can get rid of it from my hard drive. I've found [[COLOR="Red"]one[/COLOR]]("http://www.ngine.de/article/id/8") or [COLOR="Red"][two]("http://articles.techrepublic.com.com/5100-22_11-5928902.html")[/COLOR] guides on this.

---

