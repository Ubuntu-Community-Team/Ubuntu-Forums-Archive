---
title: "New ubuntu install: now can't run XP"
date: 2009-09-20
forum: Installation &amp; Upgrades
---

### Post by oldmankit on 2009-09-20
I've just installed the latest version of ubuntu and am really impressed with it.  Most things are working right out of the box.  However, I cannot access my windows xp (SP3) installation.  When I was installing ubuntu, I tried resizing the windows partition.  It was not successful doinig that:   I don't know if that's responsible for the following error. 
 
 
The bootloader was set-up fine, but when I selected the XP partition, I got a message saying it "Windows could not start because the following file is missing or corrupt: <windows root>\system32\hal.dll.  Please re-install a copy of the above file." I looked up the problem and it seems to be to do with the boot.ini file, or mbr.  I have extracted hal.dll from the XP cd to \system32, and of course it didn't fix the problem. 
 
From the recovery console it says I have one windows partition, on D:\.  Here are my attempts to fix it, and the results: 
 
bootcfg /list  : There are no boot entries available to display. 
bootcfg /scan  : Error: Failed to successfully scan disks for Windows installations.  This error may be caused by a corrupt file syst, which could prevent Bootcfg from successfully scanning.  Use chkdsk to detect any disk errors.  Note: this operation must complete successfully in order for the /add or /rebuild commands to be utilized. 
 
I've run chkdsk /r, with no errors reported. 
 
I ran fixmbr and fixboot, both of which completed without any error reports.  The bootcfg command still wouldn't run. 
 
After that, I rebooted, and I found that it tried to go straight into windows, bypassing the bootloader that ubuntu had set-up.  (Unsurprisingly, the original hal.dll error still prevented windows loading.)  I tried to get the ubuntu bootloader running again, but resorted to re-installing ubuntu. 
 
So now I'm back at square one.  Ubuntu is running fine, the windows parition is sitting there prettily but uselessly.  I've spent a good deal of time searching for a solution, and the answer seems to be re-install windows XP.  That seems so heavy-handed and I'd really like to find a solution to this.  However I feel I've exhausted all the answers on existing forums. 

One last thing.  There is no boot.ini file on the windows partition.  On the windows partition, I only found a 'bootex.log' file, contents here:
> Checking file system on \DosDevices\D: 
The type of the file system is NTFS. 
 
The volume is dirty. 
Cleaning up minor inconsistencies on the drive. 
Cleaning up 2744 unused index entries from index $SII of file 0x9. 
Cleaning up 2744 unused index entries from index $SDH of file 0x9. 
Cleaning up 2744 unused security descriptors. 
CHKDSK is verifying Usn Journal... 
Usn Journal verification completed. 
CHKDSK discovered free space marked as allocated in the 
master file table (MFT) bitmap. 
Correcting errors in the Volume Bitmap. 
Windows has made corrections to the file system. 
 
  46082420 KB total disk space. 
  20136136 KB in 98834 files. 
     43104 KB in 8522 indexes. 
         0 KB in bad sectors. 
    189000 KB in use by the system. 
     65536 KB occupied by the log file. 
  25714180 KB available on disk. 
 
      4096 bytes in each allocation unit. 
  11520605 total allocation units on disk. 
   6428545 allocation units available on disk. 
 
Internal Info: 
c0 a4 01 00 68 a3 01 00 ff 66 02 00 00 00 00 00  ....h....f...... 
07 46 00 00 01 00 00 00 cf 1c 00 00 00 00 00 00  .F.............. 
c8 bd 45 02 00 00 00 00 52 5b a7 55 00 00 00 00  ..E.....R[.U.... 
68 fc fd 24 00 00 00 00 00 00 00 00 00 00 00 00  h..$............ 
00 00 00 00 00 00 00 00 be 4c e9 7e 00 00 00 00  .........L.~.... 
99 9e 36 00 00 00 00 00 18 3b 07 00 12 82 01 00  ..6......;...... 
00 00 00 00 00 20 03 cd 04 00 00 00 4a 21 00 00  ..... ......J!.. On a separate partition where I store my documents, there is a boot.ini file, contents:
> [boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect Any suggestions are very appreciated.

PS:  On my single hard drive, I have one ntfs partition, one fat 'documents' partition, one root partition, one swap partition.  Whilst working through this problem I've noticed an 8mb partition at the start of the hard drive.  I don't remember it being there before, don't know what it is...

---

### Post by badger_fruit on 2009-09-20
> **oldmankit said:**
> IPS:  On my single hard drive, I have one ntfs partition, one fat 'documents' partition, one root partition, one swap partition.  Whilst working through this problem I've noticed an 8mb partition at the start of the hard drive.  I don't remember it being there before, don't know what it is...

That's normal. THe space is usually reserved by the HDD controller IIRC, don't worry about it, it's only 8MB ;)
As for the other problem, yes, sounds like the re-size of your partition's messed something up.
Best advice: Format HDD completely & start over.  Perhaps drop windows all together ;)

(OK, that's a joke, i know myself that there are just some things you can't do under linux, BOOOOO!)

Re-installation or fixing MBRs are beyond me but whenever I screw my systems up, i just wipe them and start again - oh and pray you made a backup of your important data, just in case.

---

### Post by oldmankit on 2009-09-20
> **badger_fruit said:**
> 
Re-installation or fixing MBRs are beyond me but whenever I screw my systems up, i just wipe them and start again - oh and pray you made a backup of your important data, just in case.

Hmmm, yes I can see that is definitely a solution, however I've finally got windows tuned and running just how I like it.  I only reinstalled it a few months ago.  I will do this as a final resort, but would find it so much more satisfying to get back into windows.  There is clearly nothing wrong with my hard disk or the installation, and it should be possible to get back in...just need the right expertise and some patience : )

And yes I sure did make a backup of everything...this isn't my first linux install!

---

### Post by hub_cap on 2009-09-20
Get a copy of "Super Grub", Grub-Rescue Disk. You can fix what ails you with this or SystemRescueCD (has many utilities).  

see here

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

and here

[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by oldmankit on 2009-09-30
> **hub_cap said:**
> Get a copy of "Super Grub", Grub-Rescue Disk. You can fix what ails you with this or SystemRescueCD (has many utilities).  

see here

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

and here

[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

Well I had a go, but it couldn't see my windows partition.  In the end, I did the proper thing and reinstalled windows.

---

