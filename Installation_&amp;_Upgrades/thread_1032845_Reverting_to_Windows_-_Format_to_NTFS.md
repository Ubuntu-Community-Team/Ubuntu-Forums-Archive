---
title: "Reverting to Windows - Format to NTFS"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by vlastanovak on 2009-01-06
Hey,

I've recently installed Ubuntu, however I would like to revert back to Windows Vista Home Premium for the time being as I need a number of programs that are only available through Windows. So I would like to remove ubuntu from my system and put Vista back on there for now. I will keep Ubuntu on the CD and run it off that when I need it.

Problem is, when I tried to reinstall Vista.. it says my partitions need to be formatted to NTFS. How do I do this? I have absolutely no idea!

Thanks in advance.

---

---

### Post by albinootje on 2009-01-06
> **vlastanovak said:**
> 
Problem is, when I tried to reinstall Vista.. it says my partitions need to be formatted to NTFS. How do I do this? I have absolutely no idea!


Boot from the Ubuntu installation cdrom, choose the "live session", open a terminal, type in :
```

sudo apt-get install gparted
sudo gparted

```
Remove the Ubuntu partition(s) from your disk.
After that install your MS-Vista installation.

---

### Post by Pumalite on 2009-01-06
You should have some partitioner that can reformat the drive to ntfs.
Maybe your Installation CD.
(sorry I'm not a Windows user.)

---

### Post by damis648 on 2009-01-06
> **albinootje said:**
> Boot from the Ubuntu installation cdrom, choose the "live session", open a terminal, type in :
```

sudo apt-get install gparted
sudo gparted

```
Remove the Ubuntu partition(s) from your disk.
After that install your MS-Vista installation.

That is not even needed. Gparted is already installed. Just head to System>Administration>Partition Manager and delete all partitions, followed by creating one large NTFS partition.

---

### Post by 2hot6ft2 on 2009-01-06
Boot from the livecd and once you're at the live desktop go to
System>Adminstration>Partition Editor
right click on the swap partition and select swapoff
right click again and select delete partition
right click on the ubuntu partition and select delete
click on the drive which should have a lot of space now and click on New
select Primary for type
Right click on it again and select Format to>NTFS

And then click on Apply

---

### Post by skern03 on 2009-01-06
> **vlastanovak said:**
> Hey,

I've recently installed Ubuntu, however I would like to revert back to Windows Vista Home Premium for the time being as I need a number of programs that are only available through Windows. So I would like to remove ubuntu from my system and put Vista back on there for now. I will keep Ubuntu on the CD and run it off that when I need it.

Problem is, when I tried to reinstall Vista.. it says my partitions need to be formatted to NTFS. How do I do this? I have absolutely no idea!

Thanks in advance.

---

You can also use Sun's VirtualBox. Use the PUEL (Public Use) version, not the OSE (Open Source Edition) to run Vista in a virtual instance under Ubuntu.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by albinootje on 2009-01-06
> **damis648 said:**
> That is not even needed. Gparted is already installed. Just head to System>Administration>Partition Manager and delete all partitions, followed by creating one large NTFS partition.

I suggested this because the OP didn't say which Ubuntu release the OP was using, and I don't remember whether gparted was already included in Ubuntu Hoary Hedgehog or Dapper Drake for example.

---

### Post by theozzlives on 2009-01-06
Since you're determined to delete everything why don't you dual boot or use WUBI. Much faster than the live CD and you can save stuff, change settings, and install software should the need arise.

---

### Post by maestrobwh1 on 2009-01-06
If you use gparted, you can actually move your ubuntu partition to the "end" or your disk.  You should then be able to install windows on the first NTFS partition.

Depending on how savvy you are, you could, then install grub for windows (google it), and add a line to the windows bootloader to call grub on the ubuntu partition.

You could also install grub on pen drive fairly easily, and if your machine boots from usb, set it to boot the eon and have the grub call the configfile for the ubuntu partition.

I am not sure if grub can call Vista if it is a post configuration like this.  I did something like this for XP, but I just reinstalled grub as my bootloader.  The NT win boot loader just isn't that configurable.

---

