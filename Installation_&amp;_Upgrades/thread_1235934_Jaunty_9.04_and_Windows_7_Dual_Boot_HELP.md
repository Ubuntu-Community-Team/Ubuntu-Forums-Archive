---
title: "Jaunty 9.04 and Windows 7 Dual Boot HELP"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by skrahel on 2009-08-09
Ok, I have been working on dual-booting Windows 7 (RC) with Ubuntu 9.04 and I keep having the same problem with all the ways I try. I have yet to use virtual box though because I want to run them separately. So, I have Ubuntu already loaded, I have the windows 7 rc iso that i burnt using k3b, and I have partitioned my hard drive through gparted. Next I try to boot Windows to install, but right before I get to the installation menu (past "press any key to bott from cd or dvd...") my system shuts off and restarts. 

I am running all of this on my Sony VAIO Notebook with these specs:
[http://www.docs.sony.com/release/specs/VGNFE660G_mksp.pdf](http://www.docs.sony.com/release/specs/VGNFE660G_mksp.pdf)

Am I able to dual-boot, am I doing something wrong, please help me.

---

### Post by merlinus on 2009-08-09
Post results of

```
sudo fdisk -l
```

so we can see your partitions and how they are formatted.

---

### Post by skrahel on 2009-08-13
shane@shane-laptop:~$ sudo fdisk -l
[sudo] password for shane: 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa17fead9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11790    94703143+  83  Linux
/dev/sda2           11791       12161     2980057+   5  Extended
/dev/sda5           11791       12161     2980026   82  Linux swap / Solaris

---

### Post by skrahel on 2009-08-13
hey merlin,
you replied to my question regarding the jaunty and win 7 dual-boot. here are my specs [i clean booted ubuntu] 

shane@shane-laptop:~$ sudo fdisk -l
[sudo] password for shane: 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa17fead9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11790    94703143+  83  Linux
/dev/sda2           11791       12161     2980057+   5  Extended
/dev/sda5           11791       12161     2980026   82  Linux swap / Solaris

---

### Post by raymondh on 2009-08-13
just some quick 2-cent thoughts ...

1.  where do you plan to install windows?
2.  windows will not read ext3 format. YOu need to create free space for NTFS
3.  remember to recover GRUB after installation.

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
[http://www.brighthub.com/computing/linux/articles/23075.aspx](http://www.brighthub.com/computing/linux/articles/23075.aspx)

Do back-up your files.  Good luck.

---

