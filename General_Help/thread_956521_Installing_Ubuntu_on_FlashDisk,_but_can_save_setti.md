---
title: "Installing Ubuntu on FlashDisk, but can save settings"
date: 2008-10-23
forum: General Help
---

### Post by phicha on 2008-10-23
I am trying to install ubuntu on my flashdisk with 2 gb space. But it is only copy the cd to flashdisk and booting from flashdisk. 

And i have make some change on settings and folder on dekstop. But after restart my settings and folder was gone.

Is there a way to install ubuntu and running ubuntu from flashdisk with out lost settings and data ?

Thanks a lot,
Phil

---

### Post by pebo on 2008-10-23
Try [this]("http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/")

---

### Post by C.S.Cameron on 2008-10-23
I prefer to install Ubuntu to flash disk the same as to HDD.
Unplug the HDD and run install from Live CD or Live USB.

However 8.10 has a tool called usb-creator that will build a persistent USB drive.

It is found in System, Administration, and called "Create a USB startup disk".

It will build a USB system in under 5 minutes, that will save your downloads and changes. It is almost fool proof to use.

It also takes up much less space on a disk than full install.

The one drawback is that upgrades to the kernel do not work.

---

### Post by phicha on 2008-10-24
thanks but when i am trying to install i get this error

root@philip-desktop:/home/philip# sudo apt-get install syslinux mtools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  floppyd
The following NEW packages will be installed:
  mtools syslinux
0 upgraded, 2 newly installed, 0 to remove and 262 not upgraded.
Need to get 557kB of archives.
After this operation, 1253kB of additional disk space will be used.
Err [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy/main mtools 3.9.11-0ubuntu1
  Could not resolve 'id.archive.ubuntu.com'
Err [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy/main syslinux 2:3.53-1ubuntu2
  Could not resolve 'id.archive.ubuntu.com'
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/main/m/mtools/mtools_3.9.11-0ubuntu1_i386.deb](http://id.archive.ubuntu.com/ubuntu/pool/main/m/mtools/mtools_3.9.11-0ubuntu1_i386.deb)  Could not resolve 'id.archive.ubuntu.com'
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/main/s/syslinux/syslinux_3.53-1ubuntu2_i386.deb](http://id.archive.ubuntu.com/ubuntu/pool/main/s/syslinux/syslinux_3.53-1ubuntu2_i386.deb)  Could not resolve 'id.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@philip-desktop:/home/philip# syslinux -sf /dev/sdb1
The program 'syslinux' is currently not installed.  You can install it by typing:
apt-get install syslinux
root@philip-desktop:/home/philip# 


what should i do ? thanks,

---

### Post by phicha on 2008-10-24
I have fixed the installation before by changing my country to australia. And it work completely fine for me.

And after i reboot my pc, and start up from flashdisk, somehow it show up start ubuntu with saving and restoring mode like. And i pick it. But it only start and showing BusyBox.

I wonder what happened ? Thanks,

---

### Post by dcstar on 2008-10-25
> **phicha said:**
> 
........
Is there a way to install ubuntu and running ubuntu from flashdisk with out lost settings and data ?


8.10 has a tool for creating "Persistent" USB disk installs built into it, have a look here:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

