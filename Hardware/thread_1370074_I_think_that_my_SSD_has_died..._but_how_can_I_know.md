---
title: "I think that my SSD has died... but how can I know for sure?"
date: 2010-01-01
forum: Hardware
---

### Post by lordtimothydexter on 2010-01-01
Any help, tips, advice, or even simple commiseration would be greatly appreciated. The SSD on my Acer seems to have kicked the bucket, taking along with it important documents related to my upcoming Ph.D. exams. I'm in dire straits! >:(

I have an Acer Aspire One ZG5 (8GB SSD + 8GB external card) with UNR 9.10 installed. One day, the OS was performing an automatic update, and then froze completely. I had to do a hard restart. When it restarted, however, it went through the BIOS screen, but then stopped with a GRUB error 21. It has been doing so ever since. I waited a few days to see if it was simply being temperamental, but it seems to be rather stubborn indeed.

I booted up with a 9.10 Live USB. Gparted recognizes sda1, but says that it has no filesystem. fdisk -l returns:

> Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaead4529

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         932     7486258+  83  Linux
/dev/sda2             933         981      393592+   5  Extended
/dev/sda5             933         981      393561   82  Linux swap / Solaris

Disk /dev/sdb: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders
Units = cylinders of 6960 * 512 = 3563520 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1126     3915752    b  W95 FAT32

Disk /dev/mmcblk0: 8017 MB, 8017936384 bytes
202 heads, 59 sectors/track, 1313 cylinders
Units = cylinders of 11918 * 512 = 6102016 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1        1314     7825920    b  W95 FAT32
I assume that sda1 is the original boot partition on the internal SSD, that sdb1 is the USB stick (it's 4GB), and that mmcblk0p1 is the external "storage expansion" SSD card. Attempting to mount sda1 returns the error "can't read superblock." In GParted, it appears without a file system and with an (!) next to it.

I went into parted /dev/sda and asked it to print, and it returned:

> Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  7666MB  7666MB  primary                   boot
 2      7666MB  8069MB  403MB   extended
 5      7666MB  8069MB  403MB   logical   linux-swap(v1)
Finally, "dmesg -i | grep sd" returns a rather frightening:

> ubuntu@ubuntu:/etc$ sudo dmesg |grep -i sd
[ 9773.096492] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9773.096504] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9773.096567] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9773.096580] end_request: I/O error, dev sda, sector 63
[ 9773.096595] Buffer I/O error on device sda1, logical block 0
[ 9773.272491] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9773.272503] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9773.272562] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9773.272575] end_request: I/O error, dev sda, sector 63
[ 9773.272590] Buffer I/O error on device sda1, logical block 0
[ 9773.508433] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9773.508444] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9773.508507] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9773.508519] end_request: I/O error, dev sda, sector 63
[ 9773.668436] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9773.668447] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9773.668510] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9773.668522] end_request: I/O error, dev sda, sector 63
[ 9773.817914] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9773.817925] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9773.817988] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9773.818000] end_request: I/O error, dev sda, sector 63
[ 9773.984501] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9773.984512] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9773.984575] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9773.984588] end_request: I/O error, dev sda, sector 63
[ 9774.245702] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9774.245714] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9774.245777] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9774.245789] end_request: I/O error, dev sda, sector 63
[ 9820.520425] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9820.520437] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9820.520499] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9820.520511] end_request: I/O error, dev sda, sector 63
[ 9820.520532] Buffer I/O error on device sda1, logical block 0
[ 9820.520543] Buffer I/O error on device sda1, logical block 1
[ 9820.520553] Buffer I/O error on device sda1, logical block 2
[ 9820.520562] Buffer I/O error on device sda1, logical block 3
[ 9820.520572] Buffer I/O error on device sda1, logical block 4
[ 9820.520581] Buffer I/O error on device sda1, logical block 5
[ 9820.520590] Buffer I/O error on device sda1, logical block 6
[ 9820.520600] Buffer I/O error on device sda1, logical block 7
[ 9820.520617] Buffer I/O error on device sda1, logical block 8
[ 9820.520626] Buffer I/O error on device sda1, logical block 9
[ 9820.760402] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9820.760413] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9820.760476] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9820.760488] end_request: I/O error, dev sda, sector 63
[ 9828.924428] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9828.924439] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9828.924502] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9828.924514] end_request: I/O error, dev sda, sector 63
[ 9828.924534] Buffer I/O error on device sda1, logical block 0
[ 9828.924546] Buffer I/O error on device sda1, logical block 1
[ 9828.924556] Buffer I/O error on device sda1, logical block 2
[ 9828.924565] Buffer I/O error on device sda1, logical block 3
[ 9828.924575] Buffer I/O error on device sda1, logical block 4
[ 9828.924584] Buffer I/O error on device sda1, logical block 5
[ 9828.924594] Buffer I/O error on device sda1, logical block 6
[ 9828.924604] Buffer I/O error on device sda1, logical block 7
[ 9828.924619] Buffer I/O error on device sda1, logical block 8
[ 9828.924629] Buffer I/O error on device sda1, logical block 9
[ 9829.112399] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9829.112411] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9829.112473] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9829.112485] end_request: I/O error, dev sda, sector 63
[ 9829.696416] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9829.696427] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9829.696490] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9829.696502] end_request: I/O error, dev sda, sector 32
[ 9861.488431] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9861.488443] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9861.488505] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9861.488517] end_request: I/O error, dev sda, sector 56
[ 9861.488537] Buffer I/O error on device sda, logical block 7
[ 9861.648708] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9861.648719] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9861.648782] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9861.648794] end_request: I/O error, dev sda, sector 56
[ 9861.648807] Buffer I/O error on device sda, logical block 7
[ 9861.808434] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9861.808445] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9861.808508] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9861.808520] end_request: I/O error, dev sda, sector 56
[ 9861.808533] Buffer I/O error on device sda, logical block 7
[ 9862.124429] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9862.124440] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9862.124503] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9862.124515] end_request: I/O error, dev sda, sector 56
[ 9862.124528] Buffer I/O error on device sda, logical block 7
[ 9862.288433] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9862.288444] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9862.288507] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9862.288519] end_request: I/O error, dev sda, sector 56
[ 9862.288532] Buffer I/O error on device sda, logical block 7
[ 9862.448429] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9862.448440] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9862.448503] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9862.448515] end_request: I/O error, dev sda, sector 56
[ 9862.448528] Buffer I/O error on device sda, logical block 7
[ 9862.592415] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9862.592427] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9862.592489] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9862.592501] end_request: I/O error, dev sda, sector 56
[ 9862.592514] Buffer I/O error on device sda, logical block 7
[ 9862.780472] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9862.780484] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9862.780546] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9862.780559] end_request: I/O error, dev sda, sector 56
[ 9862.780572] Buffer I/O error on device sda, logical block 7
[ 9862.960403] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9862.960414] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9862.960477] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9862.960490] end_request: I/O error, dev sda, sector 56
[ 9862.960502] Buffer I/O error on device sda, logical block 7
[ 9863.252610] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9863.252621] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9863.252684] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9863.252697] end_request: I/O error, dev sda, sector 56
[ 9863.252709] Buffer I/O error on device sda, logical block 7
[ 9863.410601] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9863.410614] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9863.410682] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9863.410695] end_request: I/O error, dev sda, sector 56
[ 9863.631810] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9863.631821] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9863.631884] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9863.631896] end_request: I/O error, dev sda, sector 56
[ 9863.788464] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9863.788476] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9863.788538] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9863.788551] end_request: I/O error, dev sda, sector 56
[ 9863.968416] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9863.968427] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9863.968490] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9863.968502] end_request: I/O error, dev sda, sector 56
[ 9864.136436] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9864.136448] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9864.136519] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9864.136532] end_request: I/O error, dev sda, sector 56
[ 9864.422848] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9864.422860] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9864.422922] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9864.422934] end_request: I/O error, dev sda, sector 56
[ 9864.560418] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9864.560430] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9864.560492] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9864.560505] end_request: I/O error, dev sda, sector 56
[ 9864.800433] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9864.800444] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9864.800507] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9864.800519] end_request: I/O error, dev sda, sector 56
[ 9864.944402] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9864.944413] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9864.944475] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9864.944488] end_request: I/O error, dev sda, sector 56
[ 9865.132405] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9865.132416] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9865.132478] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9865.132491] end_request: I/O error, dev sda, sector 56
[ 9865.292391] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9865.292402] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9865.292465] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9865.292477] end_request: I/O error, dev sda, sector 56
[ 9865.492456] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9865.492467] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9865.492529] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9865.492542] end_request: I/O error, dev sda, sector 56
[ 9865.664516] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9865.664527] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9865.664590] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9865.664602] end_request: I/O error, dev sda, sector 56
[ 9865.928401] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9865.928412] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9865.928475] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9865.928487] end_request: I/O error, dev sda, sector 56
[ 9866.084404] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9866.084415] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9866.084477] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9866.084489] end_request: I/O error, dev sda, sector 56
[ 9866.372562] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9866.372573] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9866.372636] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9866.372648] end_request: I/O error, dev sda, sector 56
[ 9866.540411] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9866.540422] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 9866.540485] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
[ 9866.540497] end_request: I/O error, dev sda, sector 56
I am currently running PhotoRec 6.11.3 in an attempt at forensic recovery. I started with a general sweep, and it picked up all kinds of files, including ones from past Windows installations, as well as pictures that could only have been on that hard drive. Now I'm running it such that it's only searching for .doc files, since that's all I care about -- important notes for my Ph.D. exams are on this hard drive, and I stupidly didn't print them or back them up, since I only started using it a week or so ago.

---

### Post by sailthesea on 2010-01-01
Don't Panic!:)
If an update froze the OS your /home will almost certainly be intact
 You seem to be taking the right steps although you might be overreacting
 Try the live USB again and see if you can fix the problem from there
 Whats in SDA2? Hopefully /home swap on extended 
No 
 SDA3 Swap
See how PhotoRec does 
If you can start a live session you have a good chance of getting to the data unless the SSD really is fried (I don't think it is)
Good luck!:)

---

### Post by lordtimothydexter on 2010-01-01
Thanks for the encouragement! :) I'm not at my computer at the moment, but I'll continue fiddling as soon as I get home.
 
I don't think that there is an sda3, or, at least, it doesn't appear in any of the lists. I can't mount sda1, due to the "can't read superblock" error in mount. As for sda5, I remember trying to mount it and receiving a similar error, but I'll try again. What is in these partitions, exactly? Do they store backups/memory of my /home/? I'm an experienced PC user, but a novice when it comes to hardware level stuff; also, I'm an amateur with Linux. So, any layman's explanations would be rather helpful. :)
 
PhotoRec seems, so far, to be picking up jarbled Office documents (11 so far, including an .xls that seems to function). But, do to the comparatively feeble power of the netbook, it won't finish for another 10 or so hours.
 
The question, I suppose, is did the update freeze the OS, or did the SSD crash bomb everything? Clearly, the SSD seems to be relatively intact, since it's been detected and since PhotoRec is recovering files from it. Also, GRUB does valliantly try to boot the OS before sputtering and crashing (I assume that, if the drive were totally dead, GRUB wouldn't load at all). But I can't seem to mount it (so I can't access fstab or any of my files, either) -- which suggests that it isn't a GRUB issue, no? I wouldn't be able to replace GRUB if I wanted to, since I can't access the file system.
 
Why can't any of the partition managers read the file system? Doesn't this suggest that the drive has been corrupted or damaged?
 
Thanks so much! Any help is much appreciated! :D

---

### Post by tgalati4 on 2010-01-01
It's possible that when it froze, the SSD controller had actually locked up due to the large system update.  That could have messed up the partition table.

Recreating the partition table with cfdisk or gparted using your best guess as to what the partitions should be might get you back in business.

If you can boot from a USB stick or USB CDROM, then try to mount the drive and explore it.  If you can't mount it, then post the dmesg errors.

Photorec might be your best method of recovery.

You might be better off with a used Thinkpad.  Those Aspires are one step above toys in construction.

---

### Post by lordtimothydexter on 2010-01-01
I used to have a beloved ThinkPad 600E before it was accidentally dropped and died. I got the netbook as a hand-me-down.

The dmesg results are posted above. When I attempt to mount the drives, I get a "can't read superblock" error. When I try to mount /dev/sda5 (the swap partition, I think), it tells me that it's already in use, but I can't seem to find it anywhere.

Thanks again.

Edit: GParted screenshot attached.

---

### Post by lordtimothydexter on 2010-01-02
I couldn't figure it out. Basically, the Ubuntu automatic update corrupted the file system. I had to wipe everything with an install of a lite version of Windows 7, which actually seems to be working better than Ubuntu on this particular machine (even if it's taking up much more space).

It was a fun, if time-consuming, learning experience, however. Now I've got GParted on a live USB handy for whenever I might need it. :D It's already helped me trim Windows 7 quite a bit and restore a corrupt flash drive. So, silver lining...

---

### Post by sailthesea on 2010-01-02
Was just reviewing this :(
 Sorry you didn't get a good resolution but you at least may have gained something
 From the looks of it you drive was a real jumble of primary and extended partitions in no particular order Hence Grubs failure once the original corruption occurred What the cause of that was may not be known but I would guess its update related (personally I rarely update, and instead reinstall the latest image of the OS It is much more reliable  
 I hope you managed to recover your files 
 If I've said it 3 times I've probably said it 33,000 times
Back up Back up Back UP!!:)
 May Good Fortune go with you

---

### Post by lordtimothydexter on 2010-01-02
Thanks! I'm usually OCD about backing up my documents. Main computer, netbook, flash drive, backup external HD, and server -- usually each of these things has a copy. It was just a freak incident where I had these documents on the computer only for a couple of days when the crash happened. I wasn't able to recover any of the files I needed -- as you've noted, the drive was a total mess. Oh, well.

Windows 7 seems to work much, much better on this particular netbook than UNR 9.10, in any case. Fortunately, I get free licensing from my university!

You're right about updates -- I should have turned them off, but I'm a neophyte with Linux, so I figured that I ought to do what the OS wanted me to do. I've *always* had problems with them.

---

### Post by lordtimothydexter on 2010-01-02
Thanks! I'm usually OCD about backing up my documents. Main computer, netbook, flash drive, backup external HD, and server -- usually each of these things has a copy. It was just a freak incident where I had these documents on the computer only for a couple of days when the crash happened. I wasn't able to recover any of the files I needed -- as you've noted, the drive was a total mess. Oh, well.

Windows 7 seems to work much, much better on this particular netbook than UNR 9.10, in any case. Fortunately, I get free licensing from my university! (Although now I'm beginning to understand why Linux users get annoyed with Windows -- I have GParted on hand on a USB stick for when I want to make changes that Windows otherwise makes me go through 1,000 hoops to do. Very handy!)

You're right about updates -- I should have turned them off, but I'm a neophyte with Linux, so I figured that I ought to do what the OS wanted me to do. I've *always* had problems with them.

---

### Post by teward on 2010-01-02
I'd like to make an observation:  The system says "I/O error."  Usually that's indicative of some sort of hard drive failure or device failure.  You *might* be able to access the files, but its a slim chance.  I've encountered this issue with flash drives, hard drives, etc. and have yet to find a way to repair it.

---

### Post by wyliecoyoteuk on 2010-02-21
Reading through this, it was probably not hte update that did the damage, but the hard reset.
I have an AA1, and sometimes the update process seems to freeze, but it is just taking a very long time.

I have always updated, since day one with UNR, and have had no problems.

---

