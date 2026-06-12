---
title: "Help, I cant boot windows!!! (should be sticky)"
date: 2008-08-29
forum: General Help
---

### Post by Mgiacchetti on 2008-08-29
If you're reading this, you probably think you have lost windows.

do not worry, there are many things you can do to recover your boot order.

you can follow [this]("https://help.ubuntu.com/community/WindowsDualBoot")
or 
if (which is probably the case) you have already installed ubuntu, and are having problems with grub not seeing windows...

Grab your xp cd.
insert it into the cd rom.
restart and press any key to boot from the cd

Whilst in the setup process, windows will ask you to hit a key corresponding to the "Recovery Console"  hit that key (i think its R)

log in to your existing installation and type this 

```

fixmbr

```hit enter.

Now restart and remove the xp cd and insert your ubuntu cd, and at the menu select the option to run the Live CD.


Open a Terminal

Type " sudo grub" which makes a GRUB prompt appear.

Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

Type "root (hd0,1)".

Type "setup (hd0,1)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,1)".

Type "quit".

Restart the system.


now, remove the ubuntu disk and you will notice you can still only boot to one OS, but now its XP

so.  grab [this]("http://www.winimage.com/bootpa26.zip") and unzip it to c:\bootpart

now do:
start > run > cmd

In the command prompt do:
```

cd c:\bootpart
bootpart

```will list a number of partitions
```

Physical number of disk 0 : 89799
 0 : C:* type=83  (Linux native), size= 19535008 KB, Lba Pos=63
 1 : C:  type=b  (Win95 Fat32), size= 19792080 KB, Lba Pos=39070080
 2 : C:  type=5  (Extended), size= 875542 KB, Lba Pos=78654240
 3 : C:  type=82   (Linux swap), size= 875511 KB, Lba Pos=78654303
Physical number of disk 1 : d1e0d1e0
 4 : D:* type=7  (HPFS/NTFS), size= 120053713 KB, Lba Pos=63
Physical number of disk 2 : ffffffff
 5 : E:* type=7  (HPFS/NTFS), size= 312568641 KB, Lba Pos=63

```Find the one which corresponds to your ubuntu partition (Linux Native in this case it will be 0) and type 
```

if your part number is LBA
bootpart 0 LBA ubuntu.lnx Ubuntu Hardy Heron

If the above isnt true
bootpart 0 ubuntu.lnx Ubuntu Hardy Heron

```Now, press enter, and it will save the boot information from your ubuntu partition as ubuntu.lnx in c:\bootpart and add the corresponding entry to boot.ini with the option of "Ubuntu Hardy Heron" at your NTLDR screen.

This is currently a workaround and will forward you to grub, which you are now free to remove windows from, as I have, I only use it for kernel selection.

---

### Post by fedex1993 on 2008-09-01
you might want to move this to the tutorials place it might help more people there :)

---

### Post by Shininggg on 2008-09-01
or get a super grubdisk that does all that for you.... :)

---

### Post by Oldsoldier2003 on 2008-09-01
> **fedex1993 said:**
> you might want to move this to the tutorials place it might help more people there :)

There are already tutorials on the subject in T&T :)

---

