---
title: "Yet another &quot;Windows can't detect my ext3&quot;"
date: 2009-11-17
forum: Hardware
---

### Post by rmlrml on 2009-11-17
Hello all,

I've searched through these forums and the internet a bit and keep finding the same 4 suggestions:

Ext2 IFS for Windows at fs-driver.org
LinuxReader at diskinternals.com
Ext2FSD at ext2fsd.com
explore2fs at chrysocome.net

I've tried each of these and none of them are working for my Maxtor external USB hard drive which is filled with music.  All I'm trying to do is bring this music to work so I can listen to something besides crappy radio (or pandora which is normally ok but i'm tired of it for the moment).  No biggie but it's frustrating that I can't get this to work.  Do any of those 4 options even claim to work for external USB hard drives?

any help is appreciated

Thanks

---

### Post by Anonymousable on 2009-11-17
> **rmlrml said:**
> Hello all,

I've searched through these forums and the internet a bit and keep finding the same 4 suggestions:

Ext2 IFS for Windows at fs-driver.org
LinuxReader at diskinternals.com
Ext2FSD at ext2fsd.com
explore2fs at chrysocome.net

I've tried each of these and none of them are working for my Maxtor external USB hard drive which is filled with music.  All I'm trying to do is bring this music to work so I can listen to something besides crappy radio (or pandora which is normally ok but i'm tired of it for the moment).  No biggie but it's frustrating that I can't get this to work.  Do any of those 4 options even claim to work for external USB hard drives?

any help is appreciated

Thanks
Explain the problem with ext2fsd... That works perfectly for me.

On a side note, you have a pandora... Wow, lucky.

---

### Post by rb0171610 on 2009-11-17
> **rmlrml said:**
> Hello all,

I've searched through these forums and the internet a bit and keep finding the same 4 suggestions:

Ext2 IFS for Windows at fs-driver.org
LinuxReader at diskinternals.com
Ext2FSD at ext2fsd.com
explore2fs at chrysocome.net

I've tried each of these and none of them are working for my Maxtor external USB hard drive which is filled with music.  All I'm trying to do is bring this music to work so I can listen to something besides crappy radio (or pandora which is normally ok but i'm tired of it for the moment).  No biggie but it's frustrating that I can't get this to work.  Do any of those 4 options even claim to work for external USB hard drives?

any help is appreciated

Thanks
Correct me if I am wrong, but this is software that you want to install on a Windows machine so that you can read a Linux partition? It sounds to me as if you are asking in the wrong forums.  I would suggest you use gparted, possibly with a livecd, to make a second partition on your external drive.  Vfat can be read in Windows and Linux.  Copy your music files here so that you can access them at work.  If you are having problem with these specific softwares, you should be asking on the websites of the software provider.

---

### Post by louieb on 2009-11-17
Check the inode size of the partition your try to access. IIRC none of the windows ext3  readers such as ext2ifs will work with an inode size greater that 128.

```
sudo tune2fs -l /dev/sda2 | grep Inode
```from [http://www.cyberciti.biz/faq/linux-show-contents-of-filesystem-superblock-inode/](http://www.cyberciti.biz/faq/linux-show-contents-of-filesystem-superblock-inode/)

---

### Post by coffeecat on 2009-11-17
> **louieb said:**
> Check the inode size of the partition your try to access. IIRC none of the ext3 windows readers such as ex2ifs will work with an inode size greater that 128.

A 256-byte inode is the default in ext3 systems created in Jaunty/Karmic and I'm fairly sure it was the default in Intrepid as well. This reminds me of the debacle that affected a couple of other distros (*cough* Fedora *cough*) about 18 months ago where the installer created an ext3 partition with 256-byte inodes, but the grub version shipped with the installer hadn't been patched and could only cope with 128-byte inodes. People eager to boot up into their shiny new installations were greeted with grub error 2. Except those that had the foresight to create a separate ext2 /boot partition. Oh, I remember now. It was Foresight Linux that was the other distro affected. :rolleyes: 

:p

---

### Post by rmlrml on 2009-11-22
> **louieb said:**
> Check the inode size of the partition your try to access. IIRC none of the windows ext3  readers such as ext2ifs will work with an inode size greater that 128.

```
sudo tune2fs -l /dev/sda2 | grep Inode
```from [http://www.cyberciti.biz/faq/linux-show-contents-of-filesystem-superblock-inode/](http://www.cyberciti.biz/faq/linux-show-contents-of-filesystem-superblock-inode/)

yeah i guess i am going to the wrong forum, but the help is appreciated anyway.  thanks for the responses

i tried that code and got this:

tune2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2

---

### Post by coffeecat on 2009-11-23
> **rmlrml said:**
> tune2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2

Is the ext3 partition your Maxtor external drive? That won't be /dev/sda2 - more like sdb1 or sdc1. You will need to change sda2 to the device number for the ext3/4 partition you are trying to get the inode size for. This is the sort of output you'll get (my Karmic ext4 root partition):

```
$ sudo tune2fs -l /dev/sda7 | grep Inode
Inode count:              4063472
Inodes per group:         8176
Inode blocks per group:   511
Inode size:              256
```> **rmlrml said:**
> yeah i guess i am going to the wrong forum

Not really. I don't understand why members get offended by Windows questions that affect Ubuntu. The Windows and other OSs forums were removed a few months ago, but where the OP is using both Windows and Ubuntu and needs help for some compatibility problem there are more than enough members able and willing to help.

---

