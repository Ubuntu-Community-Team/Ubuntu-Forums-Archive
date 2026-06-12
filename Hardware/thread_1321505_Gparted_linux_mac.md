---
title: "Gparted linux mac"
date: 2009-11-10
forum: Hardware
---

### Post by tomharto on 2009-11-10
Im following the instructions for installing a new harddrive and it says use ext3 for ubuntu only or fat32 for ubuntu/windows but what should i use if i want to use it for ubuntu and mac? Thanks

---

### Post by coffeecat on 2009-11-10
Is this an external drive to be able to use with both a Mac or Ubuntu machine, or a shared partition?

Whatever - your choices:

FAT32 - works out of the box in both MacOS and Ubuntu. Disadvantages: ancient, non-journalled and fragile filesystem. Maximum 4GB file size, so limiting if you are transferring video files.

HFS+ - Beware: Ubuntu/Linux can read the journalled version of hfs+, but cannot write to it. Use the non-journalled version of hfs+ and you can read/write in both OSs, but you have the disadvantage of a non-journalled fs. Beware also - you will run into permission problems because your UIDs will be different in MacOS and Ubuntu, and hfs+ supports Unix permissions (obviously). When you write files from either OS, simply adjust the permissions to make them readable/writeable by all and you should be OK. But tedious.

**Edit:** also beware if you are using Gparted to create a hfs+ partition. First - I think you need some hfs utilities installed before Gparted can create hfs partitions. Look for hfs* packages in Synaptic. Second - Gparted will create a hfs+ partition with an msdos partition table if you let it - which is a strange beast. I may be remembering incorrectly, but when I tried this, I think MacOS didn't like it. You're better off using Disk Utility in MacOS. This will create an Apple partition table which again, iirc, Ubuntu can cope with. 

NTFS - Ubuntu can read/write but MacOS only read out of the box. You can install ntfs-3g in MacOS to make it NTFS writeable, but last I read there was a significant problem with ntfs-3g in Snow Leopard. I have not installed ntfs-3g on my Mac so I have no experience of it. Also - if you are going to use NTFS, you really need Windows handy in case the filesystem journal gets damaged and you need to do a chkdsk. There are NTFS tools in Linux, but sometimes you just need Windows' chkdsk.

---

### Post by tomharto on 2009-11-10
Ok let me expand a bit more , my first post wasnt very clear :P

The HDD is internal in the ubuntu machine, and i want it so my mac can connect to the drive, read and write to it and i need the ubuntu machine to also be able to read and write to it too.

Hope thats abit clearer :)

---

### Post by coffeecat on 2009-11-10
> **tomharto said:**
> Ok let me expand a bit more , my first post wasnt very clear :P

The HDD is internal in the ubuntu machine, and i want it so my mac can connect to the drive, read and write to it and i need the ubuntu machine to also be able to read and write to it too.

Hope thats abit clearer :)

I think so. It sounds as though you need to set up a share. Then the filesystem is irrelevant. The easiest way is by setting up a samba share.

You can create a shared folder in your home folder, and then create a symlink to the partition you want to share in the shared folder. Once you've got the share up and running, your Mac can connect to it and read and write to it - so long as you set the permission right.

To create a share in Ubuntu, make a new folder in your home, right-click on it and select 'sharing options'. It's fairly easy thereafter. It will have to download and install some samba stuff, and you will have to logout and login again before the share works. And if you need help setting up a share to your other partition, post details of exactly what it is, the mount path to it, and I'll tell you how to do it. You can even do it in the GUI - no terminal stuff if you don't want.

**Edit:** by the way, you can the same in the reverse order. You can set up a shared folder in your Mac - I'm sure you know how to do it. :p Choose 'cifs', 'smb', 'samba' or 'Windows' share - I can't remember how MacOS describes it.

---

### Post by tomharto on 2009-11-10
Ii will try that later, but at the minute i cant access my driveeven  on my ubuntu box so im following [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) , I'im at the section 

4) Now decide on a filesystem. Use "ext3" if the drive will only be used with Ubuntu. For file-sharing between Ubuntu and Windows, you should use "fat32." If you are unsure, search around the wiki and forums for advice.

I just dont wanna use a wrong filesystem and mess up the HDD.

---

### Post by coffeecat on 2009-11-10
> **tomharto said:**
> 4) Now decide on a filesystem. Use "ext3" if the drive will only be used with Ubuntu. For file-sharing between Ubuntu and Windows, you should use "fat32." If you are unsure, search around the wiki and forums for advice.

The advice is good-ish, (it's dated) but you have to take it in context. This is often misunderstood. Ask yourself the question: am I using Windows on that machine as well as Ubuntu? Ignore any other machines fro the moment. If the answer is yes, then you need FAT32. Actually, these days, with good NTFS read-write support in Ubuntu, you're better of with NTFS. I'm surprised that howto is so out of date. If the answer is no, then choose ext3 (or ext4). The ext* series are Linux-native filesystems. Choose them if you only have Ubuntu or Linux **IN THAT BOX**.

Now you want MacOS to read/write that drive. I assume from what you say that MacOS is on another machine, and you want it to read/write over the network. In that case you set up a share - as I've said. In fact MacOS doesn't do any writing or reading of the share directly. It simply sends data to/from Ubuntu and Ubuntu does the reading/writing. That is why the filesystem is irrelevant when you share over the network.

**Edit:** oh, by the way...

> **tomharto said:**
> I just dont wanna use a wrong filesystem and mess up the HDD.

You won't mess up the HDD. If you get the filesystem wrong, simply backup your data (if any) and reformat to another filesystem.

---

### Post by tomharto on 2009-11-10
Ive formatted it to Ext3 format, but it says i dont have enought rights to create a folder or do anything with it, is there something i need to do to allow me to right to it? My account is the only one on this machine.

---

### Post by coffeecat on 2009-11-10
> **tomharto said:**
> Ive formatted it to Ext3 format, but it says i dont have enought rights to create a folder or do anything with it

That's right - at the moment it's owned by root. Try the following.

Assuming the mountpoint for the drive is /media/mynewdrive (as in the howto), open a terminal and:

```
sudo chown yourusername: /media/mynewdrive
```

Obviously, substitute your login name for "yourusername" and don't forget the colon.

That should work, but if it doesn't there's another workaround.

---

### Post by tomharto on 2009-11-10
I just ran that line but nothing changed, i still cant create a folder in the drive, weird...

EDIT: do i need to restart my box for the changes to work?

EDIT2: Just tried root account and it works on there, and when i switched back to my default account it works on there too.

Thanks for putting up with my silly questions :)

---

