---
title: "Install Linux to External HDD"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by Drummm on 2009-09-05
I have a 250GB USB HDD Lying around for School, 
I was wondering if it would be possible for me to install a Linux Distro to it, without reformatting to ext2/3/4. Fat32 Maybe ? 

If it isnt possible, I will just add a Live Distro, But I Would prefer to install it like the USB HDD, was a HDD inside my computer.

---

### Post by stlsaint on 2009-09-05
you can format that xthdd then create a partition for ubuntu then install it to that partition. then format the other half left over as ntfs for school work. also when installing make sure that you remove the hdd out of the system that you are using to install ubuntu to xthdd. now i suggest that you do a little more research as i have never actually done it.

---

### Post by presence1960 on 2009-09-05
> **Drummm said:**
> I have a 250GB USB HDD Lying around for School, 
I was wondering if it would be possible for me to install a Linux Distro to it, without reformatting to ext2/3/4. Fat32 Maybe ? 

If it isnt possible, I will just add a Live Distro, But I Would prefer to install it like the USB HDD, was a HDD inside my computer.

FAT & NTFS are windows filesystems. Linux will not run on them. You must format the Linux partition(s) to ext2, ext3, ext4, reiserfs or another linux filesystem.

---

### Post by Drummm on 2009-09-06
How does wubi work then ? :P

---

### Post by Bucky Ball on 2009-09-06
Installs within Windows. (w=windows; ub=ubuntu;i=installer)

---

### Post by AmerNewbieInDE on 2009-09-06
if your pc can boot from usb, it would be no problem to put linux on an external. i ran mine that way for awhile.

in gparted, format half the external ext3 for linux, mark it as boot, then create a extended partition maybe 4G, in the extended part create a linux-swap. Boot the pc with your linux disk and choose to install it to the external ext3 partition, on step 7, choose advanced and put grub on the external.

I set my pc to boot first from the usb in the bios. if the external is pluged in, it boots to linux, if it is not pluged in, it boots directly to windows as normal. I had not problem running it this way.

---

