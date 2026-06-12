---
title: "How do you setup a WinXP / Ubuntu dual boot?"
date: 2005-11-18
forum: General Help
---

### Post by Listoff78 on 2005-11-18
Hello all.  I'm a long-time IT guy doing the Windows thing.  I took my laptop from home, trashed WinXP and loaded Ubuntu.  I love it.  But, there are some things Windows does that Ubuntu doesn't (and vise-versa).  So, getting to my point...

How do I:

1) get Windows XP and Ubuntu on the same system
2) give me a choice of which OS to boot to at bootup
3) have neither OS interfear with the other in any way

I'm going to wipe this drive completely clean and start from scratch, as if it were a new drive out of the box.  How do I do this?

Thank you so much in advance for your help!
- Mike

---

### Post by xequence on 2005-11-18
Install XP first. Use fat32 if you want ubuntu to be able to read and write.

Then use the ubuntu installer to resize the XP partition to what you want it to be. Install ubuntu and let it install grub.

Now whenever you boot up it will give you a choice between ubuntu and XP. They wont affect each other.

Also if you want to you can make a seperate partition before or after ubuntu that is fat32 so you can share files between both of them.

---

### Post by cstudent on 2005-11-18
I didn't know you could change the partition once the OS was installed. I thought that it would destroy the data. Is there something more to it? Does it have anything to do with LVM? 

Bill

---

### Post by Dr. Nick on 2005-11-18
What may be easier is to install XP first and only partition part of the drive and leave the rest unpartitioned and let ubuntu partition that up for you. Use fat32 on windows if you want linux to write to it, if you dont want that then use ntfs since linux cant write to that. 

I think lvm only works on certain filesystems, I am not sure

---

### Post by sailor420 on 2005-11-18
[QUOTE=cstudent]I didn't know you could change the partition once the OS was installed. I thought that it would destroy the data. Is there something more to it? Does it have anything to do with LVM? 

Bill[/QUOTE]

You can do it, but it carries risk with it. Make sure the drive is well-defragged, and back up your data. I've done it a few times without a problem, but I've heard plenty of horror stories...

To the OP, the Ubuntu installer will set everything up for you... Install XP first, defrag, then run the Ubuntu installer, resize the partition to give you room for Ubuntu, and let it install GRUB...

---

### Post by matthew on 2005-11-18
Best link I know of to help you: [https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)

---

### Post by Listoff78 on 2005-11-18
Ok.  Makes sense.  How do I install grub?  Am I correct in assuming it will see the previous XP install and install automatically?

I've only played with Linux for two days, so it may be a little bit before I catch on!  :-)  But, I am so looking forward to getting down and dirty and learning!

Thank you for your help and patience!
Mike

---

### Post by Listoff78 on 2005-11-18
Oh, thanks Matthew.  That 'splains it!  :-)

Thank you all for your help!
Mike

---

### Post by Dr. Nick on 2005-11-18
IF your wiping the entire hd install windows and make 1 partiton the size you want and leave teh rest as free space. Boot windows to make sure it works and if it does put ubuntu in and it should partition the free space leaving XP untouched, Grub will be instaled from the ubuntu installation. Id recoment putting it on the MBR and it should add a entry to XP for you

---

### Post by aberry7670 on 2005-11-18
I have the similar kind of setup that you want. I installed XP about a year ago. Then a month ago I installed Ubuntu 5.10. The GRUB boot loader recognizes the Windows XP OS and adds an entry for it in the boot loader menu. I have tried this and it works just fine. Now I have the two OS's dual booting on the same HDD.

The only thing I did different is that I partitioned the HDD using XP. I have four partitions the first is for the XP OS and the 2nd & 3rd is for data and the 4th partition I used to install Ubuntu. I have to tell you that if not already then in the coming few years Ubuntu would be an ideal alternative to Windows OS.

Enjoy!

---

### Post by cstudent on 2005-11-18
The forums have been especially educational for me today. I have learned several new things. Does anyone know about LVM? I'm planning on upgrading my main system over the holiday weekend to Breezy. When I do I'm installing a second hard drive. I'll then have a 40gb and a 30gb. I'm wanting the 30 to be my /home directory. What little I think I know about LVM is that I can make Ubuntu "see" both drives as if they are one drive so-to-speak. And that I can go back and adjust space sizes for / and for /home. Is that correct? Or am I way off?

Bill

---

### Post by aysiu on 2005-11-18
I'm amazed no one's linked to [this tutorial](http://users.bigpond.net.au/hermanzone/) yet.

---

### Post by Listoff78 on 2005-11-18
Agreed!  It's going on my Dell Latitude D505 laptop (all hardware is recognized automatically except the internal wireless).  It has a 60 GB drive.  I'm going to do 15 for XP in NTFS, 15 for Ubuntu in EXT3, and 30 for my data in FAT32 as described above.

I just hope there is no weirdness by the two OS's reading the FAT32 partition's data.  I can't afford corruption or anything.  I can't imagine why there would be any problems.

-Mike

---

### Post by sailor420 on 2005-11-18
[QUOTE=Listoff78]Agreed!  It's going on my Dell Latitude D505 laptop (all hardware is recognized automatically except the internal wireless).  It has a 60 GB drive.  I'm going to do 15 for XP in NTFS, 15 for Ubuntu in EXT3, and 30 for my data in FAT32 as described above.

I just hope there is no weirdness by the two OS's reading the FAT32 partition's data.  I can't afford corruption or anything.  I can't imagine why there would be any problems.

-Mike[/QUOTE]

Yeah, it should be fine. Captive NTFS could be sketchy, but I've never had nor heard of problems with FAT32.

---

### Post by Pausanias on 2005-11-19
[QUOTE=Listoff78]Agreed!  It's going on my Dell Latitude D505 laptop (all hardware is recognized automatically except the internal wireless).  It has a 60 GB drive.  I'm going to do 15 for XP in NTFS, 15 for Ubuntu in EXT3, and 30 for my data in FAT32 as described above.

I just hope there is no weirdness by the two OS's reading the FAT32 partition's data.  I can't afford corruption or anything.  I can't imagine why there would be any problems.

-Mike[/QUOTE]

There should be no corruption. However, FAT32 has some important differences compared to EXT3

[list]
[*] FAT32 reading and writing is somewhat slower than ext3.
[*] FAT32 is not case sensitive. As you are a Windows guy I don't see this really being a problem for you, but it's something to be aware of.
[*] No symbolic or hard links are allowed in FAT32. This means that if you copy data over from an ext3 partition that contains symbolic links, you could get unexpected results. If you don't know what symbolic/hard links are and don't care, this shouldn't be a problem either.
[*] I seem to remember that there are no file permissions on FAT32, so if you assign permissions to files on your ext3 partition, that information may be lost when it's copied over to FAT32.
[/list]

---

