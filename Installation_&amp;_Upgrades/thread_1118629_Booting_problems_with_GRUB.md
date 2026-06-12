---
title: "Booting problems with GRUB"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by kn100 on 2009-04-07
[FONT="Arial"]Hey, got a big problem with ubuntu at the moment.
When i switched from XP to ubuntu, i made two partitions, both NTFS. One was empty, and one contained over 80gb of stuff(i did this so i wouldnt lose my massive collection of music). When i installed ubuntu it installed to the first partition and converted it to EXT3. Great. Then when it booted, worked fine for a few days, but then I realised i still had two partitions, so i transfer all my files all over to the ext3 partition, and boot up in the partition editor live cd i got off the net. Yeah great, deleted the NTFS partition, and then resized the EXT3 partition to the full HDD and made sure i didnt touch the swap partition. 
This has worked, as in live CD i see a 250gb partition, which is what i wanted. The problem is GRUB is refusing to load from the new partition for some reason. It just errors out. I don't know what to do. Any ideas?[/FONT]


FROM A LIVE CD how to i find out what my hdd is 'called' (like hd0,5) etc?

---

### Post by coffeecat on 2009-04-07
> **kn100 said:**
> [FONT=Arial]It just errors out. I don't know what to do. Any ideas?[/FONT]

Without the text of the error message I don't know what to do either. :wink:

Please post the following:

The actual error message from grub.

Now boot up with the live CD, open a terminal and post the output of:

```
sudo fdisk -l
```and

```
sudo blkid
```I suspect that this may be a UUID problem in the grub menu.lst file. You've resized the partition - this might have changed the UUID. That's why we need the output of blkid.

While you're about it in the live CD, mount your HD root partition and post the contents of /boot/grub/menu.lst from the HD installation.

By the way, the font size in your post is small. Did you change it? It's difficult to read.

---

### Post by kn100 on 2009-04-07
> **coffeecat said:**
> Without the text of the error message I don't know what to do either. :wink:

Please post the following:

The actual error message from grub.

Now boot up with the live CD, open a terminal and post the output of:

```
sudo fdisk -l
```and

```
sudo blkid
```I suspect that this may be a UUID problem in the grub menu.lst file. You've resized the partition - this might have changed the UUID. That's why we need the output of blkid.

While you're about it in the live CD, mount your HD root partition and post the contents of /boot/grub/menu.lst from the HD installation.

By the way, the font size in your post is small. Did you change it? It's difficult to read.

no i didnt change the font size, changed the font to ariel, will leave it as standard in this post. 
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
240 heads, 63 sectors/track, 32422 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xe6ad4ab1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       32422   245110288+   f  W95 Ext'd (LBA)
/dev/sda5               1          13       98185+  82  Linux swap / Solaris
/dev/sda6              14       32422   245012008+  83  Linux
ubuntu@ubuntu:~$ 



> ubuntu@ubuntu:~$ sudo blkid
/dev/sda5: UUID="9042ce29-110b-4382-8996-457640f45d20" TYPE="swap" 
/dev/sda6: UUID="7dfb5142-bbe5-4a9b-b709-b7dbe1ba2fdb" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
ubuntu@ubuntu:~$ 


If that helps? Thanks for your help, i really appreciate it. I believe its error 17,  will check now

---

### Post by coffeecat on 2009-04-07
> **kn100 said:**
> I believe its error 17,  will check now

From the grub manual:

> 17 : Cannot mount selected partitionThis error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.OK. We can't do any more until you can confirm that the grub error is 17 or something else, and we've seen the contents of /boot/grub/menu.lst from your HD installation.

---

