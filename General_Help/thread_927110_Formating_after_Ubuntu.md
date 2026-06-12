---
title: "Formating after Ubuntu"
date: 2008-09-22
forum: General Help
---

### Post by taamir on 2008-09-22
Hi, 
I tried Ubuntu on my Pc and Frankly I liked it, until it started causing problems...
now, i deleted Ubuntu but I need to format it to get rid of the boot files, do I have to make a low level format ?
or how do I make a clean start for the hard disk I used ?

(I have EASEUE Partition Manager, Win XP CD and Ubuntu CD)

Thank you

Tamir

---

### Post by Elfy on 2008-09-22
Formatting won't get rid of the boot file, it will render the pc unbootable - you need to use either xp recovery console if you installed it or the xp disc to access recovery console and use it to fixmbr first.

Then you can reformat the partition.

---

### Post by danwood76 on 2008-09-22
You simply need to remove the ubuntu partition.
If you are reinstalling XP then it will automatically overwrite the MBR.

If you had a dual boot setup and simply want to remove grub there are lots of guides around for doing this.

You basically need to boot the XP install CD and when prompted press R to go to the recovery console.
From there type fixmbr and then fixboot and it will remove grub from the MBR.

Then use a partition manager to remove the ubuntu partition and format it to what you like.

---

### Post by taamir on 2008-09-24
danwood76 I applied the fixes, but it only applies them to the Windows hard disk and partition (I used a different hard disk).

how can I make the fixes work on the other hard drive ?

---

### Post by danwood76 on 2008-09-24
To be honest you dont really need too.
If you reformat your second hard disk (ubuntu one), although the MBR will still link to grub, grub wont actually be there.
YOu can reformat the disk in  your partition manager or the windows disk manager.

The MBR is a small block at the start of your hard disk which is un accessible to you, it basically just stores the boot loader info which allows your system to boot.

As long as your BIOS is set to boot your windows disk you will never see grub again.

---

### Post by taamir on 2008-09-24
thank you.

if any one know a way to clear the MBR please tell me..
for the feeling of a brand new hard disk. and to avoid problems later.

---

### Post by danwood76 on 2008-09-24
Well in the fixmbr you can specify a drive.

```

fixmbr \Device\HardDisk0

```
So for example if you have 2 drives you would run it twice to be sure:
```

fixmbr \Device\HardDisk0
fixmbr \Device\HardDisk1

```
That will re write the MBR on to the first and second hard disk in your system.

Of course this doesnt make the drive like new it makes it have the microsoft bootloader on it, just to clear your last comment up.
It will have a similar bit of code to the grub MBR bootloader, and as I said before it doesnt matter as long as you are booting from your windows hard disk in the BIOS.

---

