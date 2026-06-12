---
title: "How  to remove Double boot"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by frmichaud on 2009-10-20
I had installed Ubuntu on the computer in my office running windows XP but the boss dont like it and I had to remove it
I removed Ubuntu with the windows control panel
How do i remove the double boot program when the computer start and reinstall a normal booting windows system?
I loved ubuntu but the boss is the boss
Please help me
Thanks
Francois

---

### Post by oldfred on 2009-10-20
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:
FIXBOOT  C:

If your system booted ok before that is all that should be required. if it did not boot add these commands.

COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
BOOTCFG  /rebuild

---

### Post by frmichaud on 2009-10-20
Thanks for the reply
The problem the computer is an HP and come only with full recovery disk not with separate windows CD so impossible to use the   recovery consol
Francois

---

### Post by mocoloco on 2009-10-20
> **frmichaud said:**
> ...I removed Ubuntu with the windows control panel...

Sounds like you installed inside of Windows using Wubi, correct? If that's what you did, then uninstalling should remove the boot option for you.  If it did not, you can remove it manually by going to Control Panel > System Properties > Advanced > Startup and Recovery (click Settings).  Click the Edit button and remove the line for Ubuntu.

---

### Post by oldfred on 2009-10-20
I think supergrub is the easiest way. 
[http://www.supergrubdisk.org/w/index.php5?title=SuperGrubDisk](http://www.supergrubdisk.org/w/index.php5?title=SuperGrubDisk)

You can also use an old win98 disk as the MBR is the same. 

Also see step 5 in this set of instructions to use testdisk from a liveCD.
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

There are also ways using Vista or Win7 repair disks bootsect.exe but you have to use specific XP command.
bootsect /nt52 C: /mbr

Bootsect.exe updates the master boot code (BS) for hard disk partitions
in order to switch between BOOTMGR and NTLDR.
You can use this tool to restore the Boot_Sector (BS) on your computer.

/nt52 Applies the master boot code (BS) that is *compatible* with NTLDR to SYS,
ALL, or <DriveLetter>. The operating system installed on SYS, ALL, or
<DriveLetter> must be older than Windows Vista.

/mbr Updates the Master Boot Record (MBR) without changing the Partition_table
on sector 0 of the disk that contains the partition specified by SYS, ALL,
or drive letter.

When used with /nt52 option, the Master Boot Record (MBR)
is *compatible* with operating systems older (XP) than Windows Vista.

When used with the /nt60 option, the Master Boot Record (MBR) is
*compatible* with Windows Vista, Windows Server 2008 or la

---

### Post by frmichaud on 2009-10-21
Thanks very much it works by removing the Ubuntu line 
Francois

---

