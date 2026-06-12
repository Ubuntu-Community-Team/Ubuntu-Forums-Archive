---
title: "Dual boot ubuntu hardy and winxp getting error: 12 with win"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by Zerosuminfinity on 2009-01-11
I'm more intermediary than absolute beginner, so be a little detailed with replies if you will 

I had to reinstall windows on my dual boot system due to virus issues. I have a drive partitioned out to have a section for XP OS then a large NTFS section for media and personal files and lastly Ubuntu OS. Upon reinstalling windows I had to rewrite the MBR so I could access Ubuntu again, after doing so XP gives me 

Error 12: invalid device requested

It seems the computer believes my media partition is my boot. fdisk -l yields:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a130a13

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        2529    20306160    f  W95 Ext'd (LBA)
/dev/sda2            2530        3988    11719417+  83  Linux
/dev/sda3   *        3989       19214   122302845    7  HPFS/NTFS
/dev/sda4           19215       19457     1951897+  82  Linux swap / Solaris
/dev/sda5               2        2529    20306128+   7  HPFS/NTFS

menu.lst lists:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

sda1 and sda5 seem to reference the same blocks, and given the size of the partition is most definitely where XP sits. 

This yields a two fold question: 1, what do I do to make grub boot the sda1/5? 2, Will doing so make the computer stop thinking of sda3 as "Boot" because there are no OS files on there at all, if not, how do I make it do that?

Ubuntu is UNable to mount either the XP or the Media partition whereas it would mount both prior to the reinstall.  

thanks

first post -wooo :guitar:

---

### Post by ajgreeny on 2009-01-11
> /dev/sda1               2        2529    20306160    f  W95 Ext'd (LBA)
/dev/sda2            2530        3988    11719417+  83  Linux
/dev/sda3   *        3989       19214   122302845    7  HPFS/NTFS
/dev/sda4           19215       19457     1951897+  82  Linux swap / Solaris
/dev/sda5               2        2529    20306128+   7  HPFS/NTFS

At the moment fdisk is seeing sda3 as your boot partition, and sda1 is an extended partition which contains sda5, perhaps your large media partition, it is hard to be sure.  If sda1 or sda5 is the partition in which your windows OS resides, you will have a problem as it is very difficult to boot windows from an extended partition, it really needs to be a primary partition.  I think this is unlikely, however, and wonder if you just need to change the line in your windows entry to

title		Microsoft Windows XP Professional
root	**	(hd0,2)**
savedefault
makeactive
chainloader	+1

This is your current boot partition sda3.  Give it a try after backing up your /boot/grub/menu.lst, just in case.

---

### Post by Zerosuminfinity on 2009-01-11
That worked! (0,2) now boots XP from the grub menu. 

However, the media partition is still seen as a system drive. I want to be able to change the drive letter of it, and windows tells me I can't change the drive letter for boot or system drives. I could [and did] change the drive letter of this partition on the previous install of windows but since reinstalling the media partition was apparently giving system/boot status. Is this removeable?

Thanks again for the help. \\:D/

---

### Post by ajgreeny on 2009-01-11
Sorry, I have no idea about that.  I almost never boot into windows any more though I retain it for the occasional use of an old scanner that is not seen by ubuntu or any other linux I've tried.  I think it has to be a case of "if it ain't broke, don't fix it!"  I assume from what you say I was right about your partitions being what I said they are?

---

### Post by Zerosuminfinity on 2009-01-11
Well changing the to hd (0,2) boots xp just fine so if that implies your were right about my drives then yes you were... Other than that I'm not sure what the extended partition refers to or how to translate that. the ~20gb [sda1/5] partition is where xp resides the ~120gb partition [sda3] is nothing but documents, pictures, and other non essential [OS] files and folders. [My] windows has a tendency to blow up a lot so i gave it a lone partition so wiping it would be easier - but of course nothing is ever easier with windows.

---

### Post by Zerosuminfinity on 2009-02-04
bumping in hopes that someone has a suggestion for changing the partition drive? 

As it stands, I can't access this drive from my linux side which renders it useless for a lot of things.

---

