---
title: "External Hard Drive problem"
date: 2008-09-01
forum: General Help
---

### Post by Alex R on 2008-09-01
Hi,

I have a 500GB Western Digital My Book external hard drive. When I first started using it on Xubuntu 8.04 it would automatically mount when I plugged it in, but now it will not mount, and I cannot find it when I type lsusb in a terminal.

How can I get it to work again?

---

### Post by joenix on 2008-09-01
I think we'll need a bit more information to help you out.
Do you know what filesystem is on the hard drive? Did you change anything to it before it stopped working?
Can you also open a terminal, attach the hard drive and type dmesg right after that? Post the output, or scan it for messages concerning a USB error or a filesystem error.

---

### Post by vanadium on 2008-09-01
The easiest to check whether your system "sees" the drive is with the command

```

sudo fdisk -l

```

or

```

sudo blkid

```

Are you sure the power of your external USB is connected in the first place?

If the drive appears in either of the above commands, and it is revealed to be ntfs formatted, then the disk was likely not properly closed by Windows. You will then need to connect the drive to a Windows system and properly disconnect the drive.

---

### Post by Alex R on 2008-09-01
Sorry, I'm not sure what the filesystem is - I haven't changed it since I got it, so I assume its one that is compatible with windows.

I don't think I've changed anything with it since it was last working (I have reinstalled xubuntu since it was last working, but I haven't changed anything relating to the external hard drive, and it wasn't working when I tried the live cd either).

After I plugged it in I don't think there were any messages relating to it in dmesg - the last 10 lines of dmesg are:

```
[  493.152598] sr 0:0:1:0: [sr0] Device not ready: Add. Sense: Medium not present
[  493.152608] end_request: I/O error, dev sr0, sector 104
[  493.305040] sr 0:0:1:0: [sr0] Device not ready: Sense Key : Not Ready [current] 
[  493.305054] sr 0:0:1:0: [sr0] Device not ready: Add. Sense: Medium not present
[  493.305065] end_request: I/O error, dev sr0, sector 104
[  497.499406] VFS: busy inodes on changed media.
[  528.334079] kjournald starting.  Commit interval 5 seconds
[  528.345914] EXT3 FS on sda2, internal journal
[  528.346118] EXT3-fs: mounted filesystem with ordered data mode.
[ 1401.776731] cdrom: This disc doesn't have any tracks I recognize!
```

---

### Post by Alex R on 2008-09-01
Yep, the power is connected. It didn't show up on fdisk or blkid - they only showed the partitions on my internal hard drive.

---

### Post by cybrsaylr on 2008-09-01
I had the same problem when using my ex HDD with XP and linux. 
You have to make sure you safely unmount it on linux when done.
The same with windows, where you have to click, 'safely remove hardware'.

If you simply pull the plug or just turn the ex HDD off it won't mount on linux the next time you go to use it.

---

### Post by vanadium on 2008-09-02
In the latter case, the drive would still show up in fdisk -l. That it does not points to a hardware problem or a bad connection.

---

### Post by indytim on 2008-09-02
Are you sure you don't have a hardware problem with the external?  You can rule this out if you can mount it in Windows.  Just a glancing thought :).

IndyTim

---

