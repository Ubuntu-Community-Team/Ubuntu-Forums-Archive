---
title: "Unknown filesystem, Grub edits and then HPFS-NTFS, can't boot anywhere!"
date: 2013-01-28
forum: Hardware
---

### Post by Forwox on 2013-01-28
People, I am in deep need for help. Hello at first.

I was cleaning my PC (folders) while working on Windows 7 (64-bit). I don't know remember actually what I did, but might be I somehow by mistake deleted Ubuntu folder, which was installed in dual boot with Win7 at the disk C (1Tb drive), disk D is for other media files.
Then I went out to clean pc from dust and so. (it's cold here, -9) But PC was already cooled down.
When I returned, I checked all cables inside before switching on PC. (disconnected drives happened earlier) And then, suddenly, where usually has been OS boot choose screen (Linux, advanced options, memory test, Windows 7) I got error message saying:
"Unknown FIlesystem"

Then I went for UBUNTU Live CD, booted in searched for problem, restarted, ejected usb (set up as live cd) and tried to run boot screen again, it gave me options as usually to choose OS, I chooesed WIndows 7, but then everything freezed on Windows 7 start up screen. :(

Then I googled for that and found that there might be something wrong with GRUB because of possibly deleted Ubuntu system folder. I made different tries to run this: 
[http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-unknown-filesystem-grub-rescue-781125/](http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-unknown-filesystem-grub-rescue-781125/) and other different GRUB fix tutorials. But I think I have messed up with partitions!
I also tried Windows 7 Recovery cd, but it gives me out this: 
*ATTACHMENT 1.*

I have also tried running TestDisk, but it shows me some kind of mess with filesystems!
There is no clear NTFS anymore, but HPFS-NTFS. (that's wrong I suppose)
+ 
I am not able to open HDD partitions on Ubuntu Live CD. (or should I) <--- **[EDIT]** fixed by writing in terminal *sudo mkdir /media/ubuntu *


I feel that I really screwed up something. 

Results of sudo fdisk -l
> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e5172d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   307202047   153497600    7  HPFS/NTFS/exFAT
/dev/sda3       307202048  1904642047   798720000    7  HPFS/NTFS/exFAT
/dev/sda4      1904644094  1951571967    23463937    5  Extended
/dev/sda5      1904644096  1943703551    19529728   83  Linux
/dev/sda6      1943705600  1951571967     3933184   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120033041920 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234439535 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd612d612

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   234416127   117207040    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders, total 15794176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9e9a7207

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    15794175     7897056+   b  W95 FAT32
I am afraid of loosing data, there are very much important things. 


Sorry for long story, but I wanted to explain how everything went to make easier find solution. I am really pleasing for help. :(

---

### Post by oldfred on 2013-01-28
Welcome to the forums.

The HPFS-NTFS is normal, it really is that it it 7 or 07 as the partition type.

I cannot see dropbox link, but you can attach screen shots with the little paperclip icon at the edit panel at the top of your message.

Your sdb shows no partitions. I would use testdisk on sdb and see if it sees any old partitions. If you repartitioned several times in may show multiple choices and you have to select a combination close to what you had or nothing overlapping with older partition.

If you get partitions back on sdb, then run this so we can see details of your system.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Forwox on 2013-01-28
*added attach.

sdb disk is actually not partitioned and is fully used for downloads. Everything related with system is on sda disk, and WIndows system is on /dev/sda2, while all music, private files stuff is on /dev/sda3. So mainly there should be problems around sda2 partition.

Here id did Boot-Repair log collection.
1. Link to boot info:
[http://paste.ubuntu.com/1584044/](http://paste.ubuntu.com/1584044/)

What's next? I am a little afraid of doing on my mine all those configurations, really important data.

---

### Post by oldfred on 2013-01-28
Nothing is mounting sda2. That often occurs if chkdsk is needed as then Linux will not mount it to prevent further damage that chkdsk may not then be able to fix.

Do not know that specific error, if chkdsk does not work then search for that error.

You now have Windows boot loader in sda and sda1 the hidden in Windows boot/repair partition looks ok, so you should be able to boot to a repair console and run Windows repairs from that.

       [http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
       
 [http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

     then you will need to reinstall grub2's boot loader to a drive and set BIOS to boot. I usually prefer to have different operating systems and its boot loader on different drives in multi-boot multi-drive systems.  That way when one drive does fail you can still boot the other drive.

---

### Post by Forwox on 2013-01-29
I really appreciate your reply and help. There is what I have explored around my problem today...

Well, there is something weird going on. After all those different attempts to fix grub I am actually able to enter Grub screen [1st attach]
Then [what's even more unbelievable] select and BOOT my Ubuntu with all settings and just as it was before all this mess! It means, I haven't deleted Ubuntu while being on Windows 7. 
BUT
It's still not possible to boot into Windows 7, when I try to boot into Windows 7 from GRUB menu, I got such error: [3rd attach]
Also it's not possible to run Windows Repair CD, because it aborts loading in the first quarter [2nd attach] and gives out error message.[4th attach]
+
From Ubuntu I can see, access, write/read data from media (D) partition [in screenshot as "Partition 3" 818Gb], but I can't open (C) [in screenshot as "Partition 2" unknown 157Gb] partition, which contains Windows 7 desktop, program files and all system stuff. Strange. [5th attach] 

Now I am able to run my Ubuntu, but still can't even run Windows Repair CD. Probably it's awful mess, but I really can't explain why it has turned out so. 

What to do now?

---

### Post by oldfred on 2013-01-29
Did you run chkdsk from your Windows repair console or a Windows repair CD? You should have a repairCD or liveCD for the current version of every system you have installed.

If booting Windows you can press f8 (Is it still f8?) to get to recovery console when booting. With grub you have to be extremely fast or try several times. Or reinstall Windows boot loader.

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Forwox on 2013-01-30
I have made bootable Windows 7 usb drive with installation. Then I came to recovery screen, but there appeared a problem, that recovery tool is impossible to see any drive where is installed Windows 7. So I found these commands, which should be entered into command promt in recovery tools section how to enable any partition by your choice as active:
> diskpart
select disk 1 (1 stays for number of disk where Win7 is)
select partition 1 (1 stays for partition where Win7 is)
active
exit

After that everything restarted and Windows 7 installation usb launched again, came to main screen, repair tools screen and there was info window about problem that has been fixed. [1st attach]
Everything restarted one more time and then went in to my Windows 7 where everything was the same as before! I am really glad that everything is fine now with both systems. It's stilla a mystery for me what crashed the GRUB.

Gazillion times of thanks for help! :)

---

