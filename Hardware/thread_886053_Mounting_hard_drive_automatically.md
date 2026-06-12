---
title: "Mounting hard drive automatically"
date: 2008-08-10
forum: Hardware
---

### Post by yadayada2 on 2008-08-10
Hmm, I don't refer to automount as when I insert a disc and ubuntu opens it automatically. Instead, what I wanna talk about is mounting a second hard drive automatically every time I use the PC. And I want to have this partition mounted to a special folder like /data.


So far I have created that folder via sudo mkdir and I have changed the permissions to my user via chown and chgrp. Now I want to tell the ubuntu OS to mount the partition into that folder permanently. And now I don't have a clou what to do.

Some pages suggest to edit the /etc/fstab, but what they show in screenshots looks different from what I get. Here I do have some entries with UUIDs and stuff like that. Furthermore I don't remember the exact file system type. Is there any GUI tool under ubuntu I could use to manage that partition mounting? I really have no interest in writing any instructions into /etc/fstab.

Thanks for any help.

---

### Post by michael1234 on 2008-08-10
"sudo gparted" from the command line is what you're probably looking for.

If you don't have gparted, just type "sudo apt-get install gparted" and then run it with the first command.

---

### Post by Yellow Pasque on 2008-08-10
Don't be afraid of the terminal. Post your /etc/fstab file and the result of these commands:
```
sudo fdisk -l
blkid
```

---

### Post by yadayada2 on 2008-08-10
> Disk /dev/sda: 20.4 GB, 20491075584 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x79457945

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2382    19133383+  83  Linux
/dev/sda2            2383        2491      875542+   5  Extended
/dev/sda5            2383        2491      875511   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15e85fe6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9733    78180291   83  Linux


blkid returned to the command line immediately without providing any information.

I will also install gparted.

---

### Post by yadayada2 on 2008-08-10
Well I have installed gparted, but I don't see how it will help me to mount a partition.

---

### Post by michael1234 on 2008-08-10
> **yadayada2 said:**
> blkid returned to the command line immediately without providing any information.

blkid is supposed to tell you what your filesystem is. Here's what I get on mine:

```
/dev/loop1: UUID="dd3dd927-b97e-4619-9e70-64067c684b0b" TYPE="ext2" 
/dev/hda1: UUID="ab59dab8-2f6a-4f94-b5f3-b2a153b9a37b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda1: SEC_TYPE="msdos" UUID="0C6F-2DED" TYPE="vfat" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="SCHOOLDISK" UUID="3805-FFC7" TYPE="vfat" 

```

I actually found this post because I am having a similar problem. It seems that I can read the files on my HD and blkid detects that hda1 has an ext3 filesystem, but I can't actually mount the logical drive within it because of a mount point error.

I am somewhat new to Linux, learning more and more each day. Gparted, while it may not let you mount things, may be able to detect the filesystem of your 80 GB sdb1 drive (your fdisk -l says "Linux" which is probably ext3). If your fstab file says something different, you may have no choice but to edit it--which shouldn't be too hard.

Run "cat /etc/fstab" and show us what it spits back.

---

### Post by yadayada2 on 2008-08-11
Actually the fstab says nothing about sdb1 :(

Thus, I have to add it, I think.

---

