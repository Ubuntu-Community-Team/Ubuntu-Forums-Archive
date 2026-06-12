---
title: "VMWARE - windows - load partition"
date: 2006-02-03
forum: Installation &amp; Upgrades
---

### Post by matsie on 2006-02-03
Hi, 

I am using a dual boot system: Ubuntu 5.10 and Windows XP on a AMD64 Sata Raid computer. 

I would like to access Ubunut also when I am using Windows. Therefore I installed the vmware player ([http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)) and the browser appliance ([http://www.vmware.com/vmtn/vm/browserapp.html)](http://www.vmware.com/vmtn/vm/browserapp.html)).

What I try to achieve is the following: 
When starting the vmware player, it should read from the existing linux partitions i have on my harddisks. 

How can that be achieved?

mat

---

### Post by MartinG on 2006-02-03
If you just want to access the files, then VMWare Workstation (which I have) allows that, but I don't know about the Player.  You might have to upgrade.

There is also, I believe, a Windows utility that allows you to access (some) Linux partitions.  You'd need to Google for that.

What is NOT possible is for VMWare Player to use an existing Linux installation in place of the custom installation (involving a .vmx file).

---

### Post by relux on 2006-06-05
I seem to recall being able to use existing OS installations in vmware workstation? I have a trial of Workstation 5.5 and I no longer see this option? It only lets me create new virtual machines.

How can i set up vmware workstation to boot my existing xp partition?

---

### Post by relux on 2006-06-07
bump..anyone?

---

### Post by jamesrw on 2006-06-16
depends on the file system... which program you can use to access files on linux partition from windows:

reiserfs: YAReg
ext2/ext3: explore2fs

as far as running the ubuntu partition from windows under vmware, I'm not sure but I'd like to know as well...

---

