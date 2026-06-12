---
title: "2nd HDD &amp; all that jazz"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by xtalgrwr on 2009-02-13
Gents,

I am an Ubuntu newbie. I added a second HDD to my system. 
Updated the BIOS.
I've leaned to do a sudo instead of a su.
That is how I got this sudo fdisk -lu file:


michael@Schroeder:~$ sudo fdsik -lu 
sudo: fdsik: command not found 
michael@Schroeder:~$ sudo fdisk -lu 

Disk /dev/sda: 160.0 GB, 160041885696 bytes 
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0x00045a1f 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *          63   303853409   151926673+  83  Linux 
/dev/sda2       303853410   312576704     4361647+   5  Extended 
/dev/sda5       303853473   312576704     4361616   82  Linux swap / Solaris 

Disk /dev/sdb: 500.1 GB, 500107862016 bytes 
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0x00000000 

   Device Boot      Start         End      Blocks   Id  System 
michael@Schroeder:~$

I was hoping someone could help me add the 2nd drive. Are those sda1,sda2,sda5 ok? 

Hopeful.:confused:

---

### Post by andrewc6l on 2009-02-13
Here's a link that explains how to do it. It's for RH8, so you'll need to put "sudo" in front of every command that's run at the [root]# prompt, but the rest should be very similar.

[http://www.yolinux.com/TUTORIALS/LinuxTutorialAdditionalHardDrive.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialAdditionalHardDrive.html)

---

### Post by Taemojitsu on 2009-02-13
random link:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

sda should be your primary hard drive. sdb will be the second hard drive. It sounds like you just need to format it with Gparted (Partition Editor).

---

### Post by xtalgrwr on 2009-02-14
Thank you for those replies.

I forgot to mention that 'all that jazz' refers to the music I want to put in the 500MB disk. I am setting this unit up as a music server with Ubuntu.
So let me do those things and report back soon.

Many thnx.

---

### Post by xtalgrwr on 2009-02-16
Andrewc61 & Taemojitsu,

Thank you for your contributions. I wobbled thu and advanced a bit. The second disk is a SCSI not an EDI so there are varyations. I wound up downloading gparted which gave me a bit of trouble with the table. It gives me a strange feeling using MSDOS for that table. Because gpt and dsb didn't work.

I think I am formatted and with fdisk I can find it. But I cannot mount because of /etc/fstab can't find it.

I thought:

#sudo mount -t /dev/sdb1 

would do it. Think I'm missing a dir and I'm not sure what to put there.

Many thanks for your help and you interest.
Thank G.d for forums!

---

### Post by Slim Odds on 2009-02-16
> **xtalgrwr said:**
> I thought:

#sudo mount -t /dev/sdb1 

would do it. Think I'm missing a dir and I'm not sure what to put there.


the "-t" requires a type argument

man mount

---

### Post by xtalgrwr on 2009-02-17
Slim Odds,

Thank you for the man mount hint.:popcorn:

I did a guesstimate and inputted:

#sudo mount -t ext2 /dev/sdb1 /root

Seems something happenend.:)

---

### Post by Slim Odds on 2009-02-17
> **xtalgrwr said:**
> Slim Odds,

Thank you for the man mount hint.:popcorn:

I did a guesstimate and inputted:

#sudo mount -t ext2 /dev/sdb1 /root

Seems something happenend.:)

```
sudo tune2fs -l /dev/sdb1
```will tell you what kind of file system is on that partition (and a whole lot more)

---

### Post by xtalgrwr on 2009-02-17
Slim Odds,

Thnx. I think I'm wasting your time and I am wasting my time.

I can do this practically blindfolded without books, forums, calls, or help in windows.

Here with all the above I'm getting nowhere. In my opinion setting up a music server in Ubuntu with two HDD should be a snap and a no-brainer.

Yes. Eventually I'll figure it out. But nowadays who has a week to set up a second HDD? Slim odds of that.

---

