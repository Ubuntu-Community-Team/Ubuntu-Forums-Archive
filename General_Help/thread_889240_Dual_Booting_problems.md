---
title: "Dual Booting problems"
date: 2008-08-13
forum: General Help
---

### Post by Zubatron on 2008-08-13
Hi all,

Here's my problem. I have Ubuntu 8.04 and Windows XP SP2 installed. Whenever I restart from either OS, when it boots back up the GRUB loader does not appear. The BIOS loads and then just a black screen. HOWever, when I shut down my PC and turn it back on the GRUB comes up just fine.

Am I missing something here?

---

### Post by Zubatron on 2008-08-14
/bump

---

### Post by Mgiacchetti on 2008-08-14
there is a work aroud that I know of but it may be different than most people would suggest and lengthy.

First [install grub]("http://ubuntuforums.org/archive/index.php/t-24113.html") on your ubuntu partition/drive (i.e. not the MBR) 
Second insert your xp cd and reboot to cd.

during the process of "setup"  you will be asked to hit "R" to go into 'Recovery Console'
Hit R

login to your xp install, and type FIXMBR
this will now replace your Master Boot Record with the windows one.

NOW
exit and restart 
REMOVE CD
You will notice you can **only** boot to windows now. (THIS WILL BE FIXED SHORTLY)
  

download [bootpart]("http://www.winimage.com/bootpa26.zip")  and unzip it to a new folder c:\bootpart

Start > Run > cmd

```

cd c:\bootpart
bootpart

```example output of above
```

C:\bootpart>bootpart
Boot Partition 2.60 for WinNT/2K/XP (c)1995-2005 G. Vollant (info@winimage.com)
WEB : http://www.winimage.com and http://www.winimage.com/bootpart.htm
Add partition in the Windows NT/2000/XP Multi-boot loader
Run "bootpart /?" for more information

Physical number of disk 0 : f8000b1
 0 : C:* type=7  (HPFS/NTFS), size= 117210208 KB, Lba Pos=63
Physical number of disk 1 : f8000b2
 1 : D:* type=83  (Linux native), size= 28748286 KB, Lba Pos=63
 2 : D:  type=5  (Extended), size= 1277167 KB, Lba Pos=57496635
 3 : D:  type=82   (Linux swap), size= 1277136 KB, Lba Pos=57496698
Physical number of disk 2 : d31bd31b
 4 : E:  type=7  (HPFS/NTFS), size= 72597703 KB, Lba Pos=63
Physical number of disk 3 : 9d9ca89f
 5 : F:* type=7  (HPFS/NTFS), size= 120045681 KB, Lba Pos=63

```in the above you would want partition 1
so

bootpart 1 c:\ubuntu.lnx LBA Ubuntu Hardy

What this will do us use bootpart to grab the bootsect of part 1 (in the list above, and using Large Block Access) save that as a file named c:\ubuntu.lnx and add a line in your boot.ini which will add a menu selection of "Ubuntu Hardy"



I know this isnt exactly what your looking for, but it works, and plus you can now remove the windows stuff from your grub, and/or hide it totally.
(personally i like it this way, i have os choice, then kernel choice for ubuntu and if someone gets on that doesnt know what they are doing, they usually choose windows :) )

---

