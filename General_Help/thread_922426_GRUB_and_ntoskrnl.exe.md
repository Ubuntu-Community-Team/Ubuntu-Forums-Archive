---
title: "GRUB and ntoskrnl.exe"
date: 2008-09-17
forum: General Help
---

### Post by dudi4155 on 2008-09-17
This problem is kinda weird for me. As long as grub is set as my bootloader, it corrupts ntoskrnl.exe file every few days with no reason and makes my windows unable to boot. Sometimes replacing ntoskrnl.exe with new one helps, sometimes I have to reinstall grub, sometimes I have to do both of these. This problem has never occured when I used standard, microsoft bootloader. 
Does anybody know solution for this problem, or can recommend any alternative bootloader? Thanks in advance!

---

### Post by LowSky on 2008-09-17
I have never heard of this happening, but searching google has turned up some interesting things

[http://www.computerhope.com/issues/ch000646.htm](http://www.computerhope.com/issues/ch000646.htm)
> 
**Keyboard issue**
This issue has also been known to be caused by a short in the ground wire in the keyboard cable. Make sure this is not the cause of your error by replacing the keyboard with a different keyboard or simply just disconnecting the keyboard from the computer. 

**Corrupt boot.ini file**
This issue is often caused when the boot.ini is missing or improperly configured. This issue often arises after a user has recently added or removed an operating system on the computer or added or removed hard disk drives in the computer.

Make sure the line pointing to the operating system and it's drive and partition is properly configured in the [boot loader] and [operating systems] section. Additional information about boot.ini can be found on document CH000492. 

[B]Missing boot.ini file
Microsoft Windows XP users:[/B] 

If the boot.ini is severely corrupted or missing a user running Microsoft Windows XP can rebuild the boot.ini to resolve this issue. Additional information about rebuilding the boot.ini can be found on document CH000648. 



---

### Post by dudi4155 on 2008-09-17
I've seen this site already, but I don't think that any of these is a problem. Here is my boot.ini file

> [boot loader]
timeout=315
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


Maybe there is other good bootloader that I can use with ubuntu and widnwos xp?

---

### Post by caljohnsmith on 2008-09-17
> **dudi4155 said:**
> I've seen this site already, but I don't think that any of these is a problem. Here is my boot.ini file
> [boot loader]
timeout=315
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOW S
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Micro soft Windows XP Professional" /noexecute=optin /fastdetect 
Maybe there is other good bootloader that I can use with ubuntu and widnwos xp?
Just to make sure your boot.ini is using the correct partition number, how about posting:
```
sudo fdisk -lu

```
I would assume it has the correct partition number, otherwise you wouldn't be able to boot at all. The erratic behavior that you describe might be hardware related, or maybe something in Windows is corrupting that ntoskrnl.exe file. Can you give any more clues of when it happens?

---

### Post by dudi4155 on 2008-09-17
```
sudo fdisk -lu
```

It returns:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           16065   359261594   179622765    f  W95 Ext'd (LBA)
/dev/sda2       359261595   360257624      498015   82  Linux swap / Solaris
/dev/sda3       360257625   381800789    10771582+  83  Linux
/dev/sda4   *   381800790   488375999    53287605    7  HPFS/NTFS
/dev/sda5           16128   161196209    80590041    7  HPFS/NTFS
/dev/sda6       161196273   273265649    56034688+   7  HPFS/NTFS
/dev/sda7       273265713   359261594    42997941    7  HPFS/NTFS

```

Is that ok?

> **caljohnsmith said:**
> I would assume it has the correct partition number, otherwise you wouldn't be able to boot at all. The erratic behavior that you describe might be hardware related, or maybe something in Windows is corrupting that ntoskrnl.exe file. Can you give any more clues of when it happens?

It happens without any reason, about two or three times a week. I always shutdown my pc correctly, but it happens only when I use grub as bootloader (I haven't tried other bootloaders though).

---

### Post by caljohnsmith on 2008-09-17
Do you know if sda4 is your Windows partition? It looks like it since that's the partition that has its boot flag set, and also, your boot.ini file would be correct for partition sda4. Did you get that boot.ini file from partition sda4? Also, what is your /boot/grub/menu.lst entry for Windows?

---

