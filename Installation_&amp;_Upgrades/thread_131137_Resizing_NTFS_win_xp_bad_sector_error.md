---
title: "Resizing NTFS win xp bad sector error"
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by qbaler on 2006-02-15
Ok so I recently decided I wanted to give ubuntu a try and learn linux.  I currently have windows xp installed on my only partition.  I tried manualy editing the partition tables with the ubuntu install cd but after i change the size.. nothing happens.  So i tried the ubuntu livecd with gparted and I get a drive busy error. I then tried linux recover cd and the pclinuxos with diskdrake and I get a bad sector error.

what do i do?

thx in advance for any

---

### Post by qbaler on 2006-02-16
bump

---

### Post by psusi on 2006-02-16
Boot into windows and go to a command prompt and run chkdsk /f /r c:

When prompted to check on the next boot, choose yes, and reboot.  Windows will check the filesystem and the disk for bad sectors.  This will take a long time.

---

### Post by qbaler on 2006-02-16
where does the log/error file go? (where do i see the results?)

---

### Post by psusi on 2006-02-16
[QUOTE=qbaler]where does the log/error file go? (where do i see the results?)[/QUOTE]

Windows will save the results in the system log iirc.

---

### Post by qbaler on 2006-02-16
THE RESULTS:

Checking file system on C:
The type of the file system is NTFS.

A disk check has been scheduled.
Windows will now check the disk.                         
Cleaning up minor inconsistencies on the drive.
Cleaning up 2 unused index entries from index $SII of file 0x9.
Cleaning up 2 unused index entries from index $SDH of file 0x9.
Cleaning up 2 unused security descriptors.
CHKDSK is verifying file data (stage 4 of 5)...
File data verification completed.
CHKDSK is verifying free space (stage 5 of 5)...
Free space verification is complete.

 117210208 KB total disk space.
  53304716 KB in 123476 files.
     40380 KB in 14204 indexes.
         4 KB in bad sectors.
    207904 KB in use by the system.
     65536 KB occupied by the log file.
  63657204 KB available on disk.

      4096 bytes in each allocation unit.
  29302552 total allocation units on disk.
  15914301 allocation units available on disk.

so now how do I get around these 4kb in bad sectors thing?

thanks for ur reply(s)

---

### Post by psusi on 2006-02-16
chkdsk flagged them as bad and so they won't be used any more.  Sometimes you can get a bad sector from things like power failures, and the sector will be fine again if you rewrite it.  If the disk actually is going bad though, usually more bad sectors will crop up and you will loose data.  

The best thing to do at this point is do a full backup, reformat the drive ( do a full format, not quick ), then run another chkdsk on it.  Maybe run it two or three times, and if it doesn't find any bad sectors then, restore and continue with resizing and installing ubuntu.  

If reformatting the drive does not make the bad sector go away, then you need to get a new disk because the problem is going to get worse.

---

### Post by qbaler on 2006-02-16
I just wiped my harddrive clean and reinstalled windows about 2 weeks ago. And last night I actualy ran a chkdsk (from the lil app) and looking back into the logs it also had 4kb bad sectors.

So would you still suggest I wipe clean again and reinstall everything? Also if I did this couldn't I just set the partitions from the begining and avoid this resizing crap?

---

### Post by psusi on 2006-02-16
[QUOTE=qbaler]I just wiped my harddrive clean and reinstalled windows about 2 weeks ago. And last night I actualy ran a chkdsk (from the lil app) and looking back into the logs it also had 4kb bad sectors.

So would you still suggest I wipe clean again and reinstall everything? Also if I did this couldn't I just set the partitions from the begining and avoid this resizing crap?[/QUOTE]


Yes, you should still reformat the drive to see if it clears the bad sector, and yes, you could just partition it the way you want from the start.  

After you backup, boot from a livecd and run sudo dd if=/dev/zero of=/dev/hda ( assuming hda is your hard drive ) and that will fill the entire drive with zeroes.  If that works, run sudo badblocks /dev/hda.  Both of these steps will take a while, but if you don't get any errors, then the drive should be clear to use and you can install windows, then ubuntu.  Just have windows install to a partition that doesn't use the whole disk.

---

### Post by qbaler on 2006-02-16
ok thx.. and tear.. i just reformated!!

linux you better be worth it! (and yes i recognize my hassle is not your fault mr. linux)

---

### Post by qbaler on 2006-02-17
ok I put in the ubuntu live cd and went to the terminal:

ubuntu@bays091-0601-dhcp037:~$ sudo dd if=/dev/zero of=/dev/hda
dd: opening `/dev/hda': Read-only file system

in gparted I have three partitions /dev/sda1 which is my ntfs, /dev/sda2 which is a locked extended of 8mb and /dev/sda5 linux-swap of 8mb.

what do I type in the terminal?

---

### Post by qbaler on 2006-02-18
ok well I did it.. and I am the now proud owner of ubuntu + winxp. Plus this seemed to fix my bad blocks!

YAY!

thank you.

---

