---
title: "How do i make my other hard drive disks appear in my desktop forever?"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by Soujiro Seta on 2007-10-24
Hey, um im trying to make my other hard drive disks appear constantly on my desktop, even after i log out, restart comp, etc. Cause if not i gotta enable them once or something, each time i run ubuntu. The only way it worked was when i installed ubuntu with manual partition editor. Stuff was showed constantly in the desktop each time i logged in.

But since i installed "guided" this last time (yup ive reinstalled ubuntu a lot of times), i can only get access to drives if i call them up in a way of speaking.

Also, if i make a link of a folder located in the drive, i cannot open it "remotely".

Any help with this?

---

### Post by simonn on 2007-10-24
/etc/fstab

man fstab

Look up fstab in Rute users guide in my sig.

---

### Post by Soujiro Seta on 2007-10-24
Kay, so i got kinda the idea. But i dont wanna screw up my disk partitions. Im not rly sure what to type in.

I think my disk are:

/dev/hba1 (windows)
/dev/hba2 (back up disk [no operative system, but windows format])

Idk what the format of windows is, and the same with back up. I think its 32 something, tho im not sure. Also the tiny two numbers idk what to put in there as well. And for the authorization thing, i also have no idea what to add! 

Some extra help, if you mind?

---

### Post by simonn on 2007-10-25
Probably the easiest way is to open a terminal and type:

```

$ ls /dev/hd*

```

Do not actually type the $, this represents the prompt. Using a $ means run this command as a normal user while using a # means run this command as root.

Paste the output here.

The way it works is like this:

/dev/hda is the first IDE hard drive
/dev/hda1 is the first partition on the first harddrive
/dev/hda2 is the second partition on the first harddrive
/dev/hdb is the second harddrive
/dev/hdb1 is the first partition on the second harddrive
/dev/hdb2 is the second partition on the second harddrive
etc etc etc

Note: To complicate things SCSI drives do things a little differently, SATA drives use the SCSI interface and, now, so do some IDE drives. In this case they use:

/dev/sda
/dev/sda1
/dev/sda2
/dev/sdb
/dev/sdb1
/dev/sdb2
etc etc

So it it probably worth doing the following as well and pasting the output here:

```

$ ls /dev/sd*

```

---

### Post by taurus on 2007-10-25
```
sudo fdisk -l
```

---

### Post by Soujiro Seta on 2007-10-25
```
$ ls /dev/hd*
/dev/hda   /dev/hda2  /dev/hdb   /dev/hdb2  /dev/hdc
/dev/hda1  /dev/hda5  /dev/hdb1  /dev/hdb5  /dev/hdd

```

```
sudo fdisk -l

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed18ed18

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5112    41062108+   7  HPFS/NTFS
/dev/hda2            5113       10010    39343185    f  W95 Ext'd (LBA)
/dev/hda5            5113       10010    39343153+   7  HPFS/NTFS

Disk /dev/hdb: 20.4 GB, 20491075584 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe401e401

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2382    19133383+  83  Linux
/dev/hdb2            2383        2491      875542+   5  Extended
/dev/hdb5            2383        2491      875511   82  Linux swap / Solaris

Disk /dev/sda: 257 MB, 257949696 bytes
16 heads, 32 sectors/track, 984 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         984      251888    e  W95 FAT16 (LBA)
```

This is what ive got.

---

