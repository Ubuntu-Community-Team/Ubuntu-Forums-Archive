---
title: "[SOLVED] External hard drive permissions"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by absolutezero1287 on 2008-02-24
I know that similar threads have been posted but after looking through them I haven't really found any answers. Here's what happened:

I was messing around with my external hard drive. I used Gparted to add an ext3 partition so that I could boot another distro from it. After finding out that my BIOS didn't allow me to boot from the USB I deleted the ext3 partition, the swap, and the extended partitions, basically returning it to how it was before...or so I thought. 

Later, I figured that I could partition my actual hard drive to boot another distro. So I decided to clear up some space by deleting my music and videos (which are all backed up in the external). Then I decided to clean out the external a bit by deleting files I deemed useless. And what happened was that I got a message saying that I didn't have permissions to write to it. I can't modify any of the files in my external in any way.

What I tried:
chown -R leonardo:users /media
I think that I was able to make myself the owner with this command but I still couldn't modify anything. The error message said that it was a read-only file system.

(Attached is a log with the output of the following commands:
fdisk-l
df -f
cat /etc/fstab

---

### Post by absolutezero1287 on 2008-02-24
Update!
I used a windows box to change the settings of the external. It didn't work. I'm allowed to move things to the trash, but I can't completely delete the files. I'm still not allowed to write to it and somehow my music has become corrupted. This really sucks. :(
Any help would be greatly appreciated!

---

### Post by konungursvia on 2008-02-24
I've seen similar issues with external drives, it's frustrating. Likely, you did some of the partiioning or drive work as root and some as user. I spent a week messing with permissions and rebooting and so on, and I have 3 external hard drives. Try this: enable sharing for the whole drive in linux. You can do this easily by downloading the KDE apps for  storage media or storage devices and sharing the external. That way all apps and all users have read write access.

---

### Post by iamaqbot on 2008-02-25
I came across this and don't know if it'll help

[http://ubuntuforums.org/showthread.php?p=4405927&posted=1#post4405927](http://ubuntuforums.org/showthread.php?p=4405927&posted=1#post4405927)

I used the gksudo command and that made all permissions good to go.

hope this helps

---

### Post by absolutezero1287 on 2008-02-26
I'm going to try....
sudo chown -R wdriver:wdriver /media/storage
ls -la /media
...I'm on a live Cd right now, but the problem is that the actual disk is marked as being read-only. It literally tells me that I can't change permissions because the disk is read-only, which it isn't.

About my music...
I was using the Gparted LiveCD to try and fix it. I went into my music backups folder and it recognized all of my files...whereas on any OS, it sees my music as being corrupted.

---

### Post by absolutezero1287 on 2008-03-11
None of the methods that I've used have worked. I'm going to write zeros to the external. We'll see how it turns out. For what it's worth, I will never use my external as a guinea pig, lol.

---

### Post by absolutezero1287 on 2008-07-04
It worked. My external is now as it was from the factory.

---

### Post by dfmalh on 2008-07-07
Hi absolutezero1287, what do you mean by "I'm going to write zeros to the external"...

*Here is my situation*: 

I bought a Seagate Barracuda 500GB SATA 32Mb Cash HD on Friday to use as an external backup HD (thesis, movies, music, etc). The HD is in an Eagle Consus case (support usb2.0 and up to 750GB HDs).

On a XP system, I could partition the Drive but I was unable to format it. Apparently there is some "time-out" error between the USB2 and the SATA connection, I am not exactly sure what it means exactly... but the bottom line is that it can't format the external that way.

I am not familiar with how to partition and format in linux (Ubuntu) so that is why I opted to go for XP... bad choice! 

I installed Gparted, and after a long struggle got all the partitions removed, and created new ones. I created 3 partitions, and formated to the FAT32 file system (as a start), checked the 3 drives and they worked, mounted correctly, in Ubuntu and on the XP system. 

So I decided to to change the first partition to ext3 file system, and one of the others to NTFS (I downloaded and installed ntfsprogs to do that). Everything fine, and everything is working. 

The drives names are however the respective sizes of each partition... that won't do, so I tried to rename them... 

I used this for the FAT32 partition: sudo mlabel -i /dev/sdb2 ::usbfat32
and this for the NTFS partition: sudo mlabel -i /dev/sdb3 -s ::usbntfs
and this for the EXT3 partition: sudo e2label /dev/sdb1 usbext3

...bad idea! now none of the drives work.

See the attached picture of the pop up window.

The ext3 and fat32 partitions are mounted, but when you try and access them, it does not work.

When I unmount the drives, I get a message that data is being written to the drive, and I can not unplug the drive. After a while the message disappear, and a new message says that it is now safe to remove drive.

In Gparted I can see the different partitions. See picture.

I included the information windows for the NTFS drive that does not want to mount and also the information window for the ext3 (first partition) which gives me a superblock error message.

I can't run a check on any of the drives, it won't work.

So, all I want to do is to delete all 3 partitions and start from scratch to create new partition.

Can anybody help with this? Please! It is very frustrating to know just enough not to be able to fix the problem. ](*,) (on the other hand it is just as dangerous)

---

### Post by absolutezero1287 on 2008-07-08
> **dfmalh said:**
> Hi absolutezero1287, what do you mean by "I'm going to write zeros to the external"...


Well, if you have important information that you want to keep than writing zeros to the drive is not the answer. It means to erase all data on the drive and replace it with null values, i.e. 0.

I'm going to guess that by creating an ext3 partition on your external you may have accidentally created a read-only drive. Basically, the computer thinks that it's an internal hard drive. In the future, don't use ext3 for storage. FAT works great and is compatible with all platforms.

---

### Post by dfmalh on 2008-07-09
Thanks absolutezero1287,

I will see if that solves the problem if I can make the drive read/write and not only have the root privileges.

I have nothing on the drive, I wanted to create a backup drive. 

The ext3 partition was that I can use rsync between my drive and the backup drive. There are issues using rsync to backup from my ext3 drive to a NTFS drive...

The other two FAT32 and NTFS would me for movies and music. 

I will see if I can make my drive read/write.

---

### Post by dfmalh on 2008-07-09
Just an update... I can't change the permission away from root...

Also I ran "dmsg" and this is the output (sorry for the long text, but I don't know how to put it in a small box that scrolls by its own :confused:):

[ 1723.355135] usb 4-4: new high speed USB device using ehci_hcd and address 3
[ 1723.472498] usb 4-4: configuration #1 chosen from 1 choice
[ 1723.652463] usbcore: registered new interface driver libusual
[ 1723.763225] Initializing USB Mass Storage driver...
[ 1723.764641] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1723.767562] usbcore: registered new interface driver usb-storage
[ 1723.767569] USB Mass Storage support registered.
[ 1723.767963] usb-storage: device found at 3
[ 1723.767966] usb-storage: waiting for device to settle before scanning
[ 1728.076135] usb-storage: device scan complete
[ 1728.076731] scsi 2:0:0:0: Direct-Access     ST350032 0AS                   PQ: 0 ANSI: 2 CCS
[ 1728.086424] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[ 1728.093781] sd 2:0:0:0: [sdb] Write Protect is off
[ 1728.093785] sd 2:0:0:0: [sdb] Mode Sense: 34 00 00 00
[ 1728.093788] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1728.097066] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[ 1728.097828] sd 2:0:0:0: [sdb] Write Protect is off
[ 1728.097832] sd 2:0:0:0: [sdb] Mode Sense: 34 00 00 00
[ 1728.097834] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1728.097837]  sdb: sdb1 sdb2 sdb3
[ 1728.119467] sd 2:0:0:0: [sdb] Attached SCSI disk
[ 1728.119510] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 1729.449559] kjournald starting.  Commit interval 5 seconds
[ 1729.451576] EXT3 FS on sdb1, internal journal
[ 1729.451581] EXT3-fs: recovery complete.
[ 1729.451585] EXT3-fs: mounted filesystem with ordered data mode.
[ 1741.799442] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1741.799451] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1741.799455] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 1741.799460] end_request: I/O error, dev sdb, sector 609784678
[ 1741.799466] Buffer I/O error on device sdb3, logical block 52441633
[ 1741.799472] Buffer I/O error on device sdb3, logical block 52441634
[ 1741.799475] Buffer I/O error on device sdb3, logical block 52441635
[ 1741.799478] Buffer I/O error on device sdb3, logical block 52441636
[ 1741.799481] Buffer I/O error on device sdb3, logical block 52441637
[ 1741.799484] Buffer I/O error on device sdb3, logical block 52441638
[ 1741.799486] Buffer I/O error on device sdb3, logical block 52441639
[ 1741.799491] Buffer I/O error on device sdb3, logical block 52441640
[ 1741.799494] Buffer I/O error on device sdb3, logical block 52441641
[ 1741.799497] Buffer I/O error on device sdb3, logical block 52441642
[ 1741.872414] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1741.872424] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1741.872428] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 1741.872433] end_request: I/O error, dev sdb, sector 305684889
[ 1741.929426] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1741.929435] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1741.929440] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 1741.929445] end_request: I/O error, dev sdb, sector 305685017
[ 1741.987835] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1741.987844] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1741.987848] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 1741.987853] end_request: I/O error, dev sdb, sector 305684889
[ 1741.988251] FAT: FAT read failed (blocknr 69)
[ 1768.072592] usb 4-4: reset high speed USB device using ehci_hcd and address 3
[ 1794.074907] usb 4-4: reset high speed USB device using ehci_hcd and address 3
[ 1794.172759] usb 4-4: device descriptor read/64, error -32
[ 1794.361573] usb 4-4: device descriptor read/64, error -32
[ 1794.550203] usb 4-4: reset high speed USB device using ehci_hcd and address 3
[ 1794.648063] usb 4-4: device descriptor read/64, error -32
[ 1794.836794] usb 4-4: device descriptor read/64, error -32
[ 1794.992728] usb 4-4: reset high speed USB device using ehci_hcd and address 3
[ 1795.018405] usb 4-4: device descriptor read/8, error -71
[ 1795.125348] usb 4-4: device descriptor read/8, error -71
[ 1795.310808] usb 4-4: reset high speed USB device using ehci_hcd and address 3
[ 1795.334065] usb 4-4: device descriptor read/8, error -71
[ 1795.438375] usb 4-4: device descriptor read/8, error -71
[ 1795.527480] usb 4-4: USB disconnect, address 3
[ 1795.539684] sd 2:0:0:0: Device offlined - not ready after error recovery
[ 1795.540167] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 1795.540173] end_request: I/O error, dev sdb, sector 10375
[ 1795.540176] printk: 117 messages suppressed.
[ 1795.540179] Buffer I/O error on device sdb1, logical block 1289
[ 1795.540182] lost page write due to I/O error on sdb1
[ 1795.540198] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 1795.540201] end_request: I/O error, dev sdb, sector 609784678
[ 1795.540204] Buffer I/O error on device sdb3, logical block 52441633
[ 1795.540208] Buffer I/O error on device sdb3, logical block 52441634
[ 1795.540211] Buffer I/O error on device sdb3, logical block 52441635
[ 1795.540213] Buffer I/O error on device sdb3, logical block 52441636
[ 1795.540216] Buffer I/O error on device sdb3, logical block 52441637
[ 1795.540219] Buffer I/O error on device sdb3, logical block 52441638
[ 1795.540222] Buffer I/O error on device sdb3, logical block 52441639
[ 1795.540560] FAT: FAT read failed (blocknr 69)
[ 1795.548700] Buffer I/O error on device sdb3, logical block 52441633
[ 1795.548707] Buffer I/O error on device sdb3, logical block 52441634
[ 1795.549678] Aborting journal on device sdb1.
[ 1795.549682] WARNING: at /build/buildd/linux-2.6.24/fs/buffer.c:1169 mark_buffer_dirty()
[ 1795.549687] Pid: 8987, comm: kjournald Tainted: P        2.6.24-19-generic #1
[ 1795.549712]  [<c01b3aea>] mark_buffer_dirty+0x7a/0x90
[ 1795.549734]  [<f895d8e0>] journal_update_superblock+0x70/0xd0 [jbd]
[ 1795.549757]  [<f895b12f>] journal_commit_transaction+0x54f/0xda0 [jbd]
[ 1795.549794]  [<c01361d7>] lock_timer_base+0x27/0x60
[ 1795.549815]  [<f895e750>] kjournald+0xa0/0x200 [jbd]
[ 1795.549831]  [<c0140c40>] autoremove_wake_function+0x0/0x40
[ 1795.549844]  [<f895e6b0>] kjournald+0x0/0x200 [jbd]
[ 1795.549854]  [<c0140982>] kthread+0x42/0x70
[ 1795.549857]  [<c0140940>] kthread+0x0/0x70
[ 1795.549864]  [<c0105677>] kernel_thread_helper+0x7/0x10
[ 1795.549879]  =======================
[ 1795.691819] usb 4-4: new high speed USB device using ehci_hcd and address 4
[ 1795.789984] usb 4-4: device descriptor read/64, error -32
[ 1795.985267] usb 4-4: device descriptor read/64, error -32
[ 1796.174657] usb 4-4: new high speed USB device using ehci_hcd and address 5
[ 1796.271852] usb 4-4: device descriptor read/64, error -32
[ 1796.460662] usb 4-4: device descriptor read/64, error -32
[ 1796.649335] usb 4-4: new high speed USB device using ehci_hcd and address 6
[ 1796.672578] usb 4-4: device descriptor read/8, error -71
[ 1796.776265] usb 4-4: device descriptor read/8, error -71
[ 1796.963974] usb 4-4: new high speed USB device using ehci_hcd and address 7
[ 1796.982483] usb 4-4: device descriptor read/8, error -71
[ 1797.088393] usb 4-4: device descriptor read/8, error -71
[ 1846.681646] usb 4-4: new high speed USB device using ehci_hcd and address 8
[ 1846.805348] usb 4-4: configuration #1 chosen from 1 choice
[ 1846.835044] scsi3 : SCSI emulation for USB Mass Storage devices
[ 1846.842522] usb-storage: device found at 8
[ 1846.842527] usb-storage: waiting for device to settle before scanning
[ 1851.073663] usb-storage: device scan complete
[ 1851.074409] scsi 3:0:0:0: Direct-Access     ST350032 0AS                   PQ: 0 ANSI: 2 CCS
[ 1851.087453] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[ 1851.088254] sd 3:0:0:0: [sdb] Write Protect is off
[ 1851.088258] sd 3:0:0:0: [sdb] Mode Sense: 34 00 00 00
[ 1851.088260] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1851.089235] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[ 1851.090001] sd 3:0:0:0: [sdb] Write Protect is off
[ 1851.090004] sd 3:0:0:0: [sdb] Mode Sense: 34 00 00 00
[ 1851.090006] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1851.090010]  sdb: sdb1 sdb2 sdb3
[ 1851.114283] sd 3:0:0:0: [sdb] Attached SCSI disk
[ 1851.114330] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 1851.888703] kjournald starting.  Commit interval 5 seconds
[ 1851.889538] EXT3 FS on sdb1, internal journal
[ 1851.889542] EXT3-fs: recovery complete.
[ 1851.889762] EXT3-fs: mounted filesystem with ordered data mode.
[ 1861.750355] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1861.750365] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1861.750369] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 1861.750374] end_request: I/O error, dev sdb, sector 609784678
[ 1861.750377] printk: 10 messages suppressed.
[ 1861.750380] Buffer I/O error on device sdb3, logical block 52441633
[ 1861.750387] Buffer I/O error on device sdb3, logical block 52441634
[ 1861.750390] Buffer I/O error on device sdb3, logical block 52441635
[ 1861.750393] Buffer I/O error on device sdb3, logical block 52441636
[ 1861.750396] Buffer I/O error on device sdb3, logical block 52441637
[ 1861.750399] Buffer I/O error on device sdb3, logical block 52441638
[ 1861.750402] Buffer I/O error on device sdb3, logical block 52441639
[ 1861.750406] Buffer I/O error on device sdb3, logical block 52441640
[ 1861.750409] Buffer I/O error on device sdb3, logical block 52441641
[ 1861.750412] Buffer I/O error on device sdb3, logical block 52441642
[ 1861.823431] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1861.823440] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1861.823444] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 1861.823450] end_request: I/O error, dev sdb, sector 305684889
[ 1861.880430] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1861.880439] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1861.880443] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 1861.880449] end_request: I/O error, dev sdb, sector 305685017
[ 1861.938736] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1861.938746] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1861.938750] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 1861.938755] end_request: I/O error, dev sdb, sector 10335
[ 1861.939125] EXT3-fs error (device sdb1): ext3_readdir: directory #11 contains a hole at offset 0
[ 1887.835684] usb 4-4: reset high speed USB device using ehci_hcd and address 8
[ 1913.807762] usb 4-4: reset high speed USB device using ehci_hcd and address 8
[ 1913.905543] usb 4-4: device descriptor read/64, error -32
[ 1914.080240] usb 4-4: device descriptor read/64, error -32
[ 1914.268985] usb 4-4: reset high speed USB device using ehci_hcd and address 8
[ 1914.373821] usb 4-4: device descriptor read/64, error -32
[ 1914.540325] usb 4-4: device descriptor read/64, error -32
[ 1914.729057] usb 4-4: reset high speed USB device using ehci_hcd and address 8
[ 1914.748267] usb 4-4: device descriptor read/8, error -71
[ 1914.853410] usb 4-4: device descriptor read/8, error -71
[ 1915.040107] usb 4-4: reset high speed USB device using ehci_hcd and address 8
[ 1915.065735] usb 4-4: device descriptor read/8, error -71
[ 1915.157922] usb 4-4: device descriptor read/8, error -71
[ 1915.247640] usb 4-4: USB disconnect, address 8
[ 1915.260055] sd 3:0:0:0: Device offlined - not ready after error recovery
[ 1915.260523] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 1915.260529] end_request: I/O error, dev sdb, sector 10375
[ 1915.260532] printk: 118 messages suppressed.
[ 1915.260535] Buffer I/O error on device sdb1, logical block 1289
[ 1915.260538] lost page write due to I/O error on sdb1
[ 1915.260553] Buffer I/O error on device sdb3, logical block 52441633
[ 1915.260556] Buffer I/O error on device sdb3, logical block 52441634
[ 1915.260559] Buffer I/O error on device sdb3, logical block 52441635
[ 1915.260562] Buffer I/O error on device sdb3, logical block 52441636
[ 1915.260565] Buffer I/O error on device sdb3, logical block 52441637
[ 1915.260568] Buffer I/O error on device sdb3, logical block 52441638
[ 1915.260572] Buffer I/O error on device sdb3, logical block 52441639
[ 1915.260579] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 1915.260583] end_request: I/O error, dev sdb, sector 63
[ 1915.260585] Buffer I/O error on device sdb1, logical block 0
[ 1915.260587] lost page write due to I/O error on sdb1
[ 1915.260713] Buffer I/O error on device sdb3, logical block 52441633
[ 1915.261347] FAT: FAT read failed (blocknr 69)
[ 1915.267539] EXT3-fs error (device sdb1): ext3_readdir: directory #11 contains a hole at offset 4096
[ 1915.268978] Aborting journal on device sdb1.
[ 1915.269004] EXT3-fs error (device sdb1): ext3_readdir: directory #11 contains a hole at offset 8192
[ 1915.271448] EXT3-fs error (device sdb1): ext3_readdir: directory #11 contains a hole at offset 12288
[ 1915.271519] ext3_abort called.
[ 1915.271521] EXT3-fs error (device sdb1): ext3_journal_start_sb: Detected aborted journal
[ 1915.271524] Remounting filesystem read-only
[ 1915.280582] FAT: FAT read failed (blocknr 69)
[ 1915.446814] usb 4-4: new high speed USB device using ehci_hcd and address 9
[ 1915.551661] usb 4-4: device descriptor read/64, error -32
[ 1915.747382] usb 4-4: device descriptor read/64, error -32
[ 1915.936998] usb 4-4: new high speed USB device using ehci_hcd and address 10
[ 1916.033973] usb 4-4: device descriptor read/64, error -32
[ 1916.229674] usb 4-4: device descriptor read/64, error -32
[ 1916.421894] usb 4-4: new high speed USB device using ehci_hcd and address 11
[ 1916.447542] usb 4-4: device descriptor read/8, error -71
[ 1916.552394] usb 4-4: device descriptor read/8, error -71
[ 1916.739923] usb 4-4: new high speed USB device using ehci_hcd and address 12
[ 1916.765602] usb 4-4: device descriptor read/8, error -71
[ 1916.875297] usb 4-4: device descriptor read/8, error -71
[ 3948.808750] usb 4-4: new high speed USB device using ehci_hcd and address 13
[ 1972.852309] usb 4-4: configuration #1 chosen from 1 choice
[ 1972.887170] scsi4 : SCSI emulation for USB Mass Storage devices
[ 1972.900221] usb-storage: device found at 13
[ 1972.900227] usb-storage: waiting for device to settle before scanning
[ 1977.220122] usb-storage: device scan complete
[ 1977.220887] scsi 4:0:0:0: Direct-Access     ST350032 0AS                   PQ: 0 ANSI: 2 CCS
[ 1977.231466] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[ 1977.232221] sd 4:0:0:0: [sdb] Write Protect is off
[ 1977.232224] sd 4:0:0:0: [sdb] Mode Sense: 34 00 00 00
[ 1977.232227] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1977.233202] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[ 1977.233968] sd 4:0:0:0: [sdb] Write Protect is off
[ 1977.233972] sd 4:0:0:0: [sdb] Mode Sense: 34 00 00 00
[ 1977.233974] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1977.233978]  sdb: sdb1 sdb2 sdb3
[ 1977.253757] sd 4:0:0:0: [sdb] Attached SCSI disk
[ 1977.253800] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 2023.809101] kjournald starting.  Commit interval 5 seconds
[ 2023.816384] EXT3 FS on sdb1, internal journal
[ 2023.816389] EXT3-fs: recovery complete.
[ 2023.816393] EXT3-fs: mounted filesystem with ordered data mode.
[ 2160.922246] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2160.922255] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 2160.922260] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 2160.922265] end_request: I/O error, dev sdb, sector 609784678
[ 2160.922268] printk: 17 messages suppressed.
[ 2160.922272] Buffer I/O error on device sdb3, logical block 52441633
[ 2160.922278] Buffer I/O error on device sdb3, logical block 52441634
[ 2160.922281] Buffer I/O error on device sdb3, logical block 52441635
[ 2160.922284] Buffer I/O error on device sdb3, logical block 52441636
[ 2160.922287] Buffer I/O error on device sdb3, logical block 52441637
[ 2160.922290] Buffer I/O error on device sdb3, logical block 52441638
[ 2160.922293] Buffer I/O error on device sdb3, logical block 52441639
[ 2160.922297] Buffer I/O error on device sdb3, logical block 52441640
[ 2160.922300] Buffer I/O error on device sdb3, logical block 52441641
[ 2160.922303] Buffer I/O error on device sdb3, logical block 52441642
[ 2160.996158] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2160.996167] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 2160.996171] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 2160.996176] end_request: I/O error, dev sdb, sector 609784678
[ 2161.052517] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2161.052526] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 2161.052531] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 2161.052536] end_request: I/O error, dev sdb, sector 609784678
[ 2161.110630] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2161.110640] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 2161.110644] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 2161.110649] end_request: I/O error, dev sdb, sector 609784679
[ 2202.531923] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2202.531932] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 2202.531936] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 2202.531941] end_request: I/O error, dev sdb, sector 557343045
[ 2202.531945] printk: 131 messages suppressed.
[ 2202.531948] Buffer I/O error on device sdb3, logical block 0
[ 2202.531954] Buffer I/O error on device sdb3, logical block 1
[ 2202.531958] Buffer I/O error on device sdb3, logical block 2
[ 2202.531961] Buffer I/O error on device sdb3, logical block 3
[ 2202.531964] Buffer I/O error on device sdb3, logical block 4
[ 2202.531966] Buffer I/O error on device sdb3, logical block 5
[ 2202.531969] Buffer I/O error on device sdb3, logical block 6
[ 2202.531972] Buffer I/O error on device sdb3, logical block 7
[ 2202.590236] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2202.590245] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 2202.590250] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 2202.590255] end_request: I/O error, dev sdb, sector 557343045
[ 2202.590260] Buffer I/O error on device sdb3, logical block 0
[ 2202.648456] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2202.648466] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 2202.648470] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 2202.648475] end_request: I/O error, dev sdb, sector 557343049
[ 2295.963453] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2295.963462] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 2295.963467] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 2295.963472] end_request: I/O error, dev sdb, sector 65
[ 2295.963836] EXT3-fs: unable to read superblock
[ 2325.360962] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2325.360972] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 2325.360976] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 2325.360981] end_request: I/O error, dev sdb, sector 65
[ 2325.361344] EXT3-fs: unable to read superblock


So, it ends in this superblock error message... I have no idea what to do. I have no data on the drive, so I can do anything to it, format, anything...

So what would you suggest I do? How do I "reset" the drive and get it to what it was when I took it out of its package?

Thanks for all the help.

---

### Post by absolutezero1287 on 2008-07-09
try this:
[code]
sudo -s
mkdir /mnt/external
EXT=/mnt/external
mount /dev/sdb1 $EXT
(replace /dev/sdb1 with w/e the partition is that you want to mount)
chown /dev/sdb1 user:user
(user:user replace with your username)

---

### Post by dfmalh on 2008-07-10
Hi absolutezero1287,

Thanks for your reply. I finally got time today to go back to the shop where I bought my HD. The first 200 sectors were bad... of course they swapped the drive for me.

Got back home, booted with Gparted Live CD and created my partitions, formatted the partitions, checked the disks etc. Not one problem! Everything worked like a charm!

For a little while there I thought it was me...

Now I just have to figure out how I can make the ext3 drive writable, as I can read/open it, but can't copy anything to it. I know it is because the rights belong to root... which would work better, if I also want to plug the drive into another system:

sudo chmod a+rw /media/DRIVENAME

or something else.

Thanks again for the help!

---

### Post by bondo101 on 2008-07-10
This may help. xp on one drive ubuntu ona second . formatted 1st drive with xp. wwent into admin tools in xp on first drive partioned xp drive so it just holds xp booted machine into ubuntu
used partion manager and partioned un alocated driveon xp drive and mounted it to be used with linux.i'm dual booting with xp and using most of the xp drive for linux. tried also usb drive with linux no luck . Trying to get 2nd sata drive on other machine with vista to work . Dell gave some help    western digital still in the dark. usb and sata to different worlds. I think its all in the Vista. xp no problems . this is just my 2 cents worth hope i helped some how
I am not familiar with how to partition and format in linux (Ubuntu) so that is why I opted to go for XP... bad choice! 

I installed Gparted, and after a long struggle got all the partitions removed, and created new ones. I created 3 partitions, and formated to the FAT32 file system (as a start), checked the 3 drives and they worked, mounted correctly, in Ubuntu and on the XP system. 

So I decided to to change the first partition to ext3 file system, and one of the others to NTFS (I downloaded and installed ntfsprogs to do that). Everything fine, and everything is working. 

The drives names are however the respective sizes of each partition... that won't do, so I tried to rename them... 

I used this for the FAT32 partition: sudo mlabel -i /dev/sdb2 ::usbfat32
and this for the NTFS partition: sudo mlabel -i /dev/sdb3 -s ::usbntfs
and this for the EXT3 partition: sudo e2label /dev/sdb1 usbext3

...bad idea! now none of the drives work.

See the attached picture of the pop up window.

The ext3 and fat32 partitions are mounted, but when you try and access them, it does not work.

When I unmount the drives, I get a message that data is being written to the drive, and I can not unplug the drive. After a while the message disappear, and a new message says that it is now safe to remove drive.

In Gparted I can see the different partitions. See picture.

I included the information windows for the NTFS drive that does not want to mount and also the information window for the ext3 (first partition) which gives me a superblock error message.

I can't run a check on any of the drives, it won't work.

So, all I want to do is to delete all 3 partitions and start from scratch to create new partition.

Can anybody help with this? Please! It is very frustrating to know just enough not to be able to fix the problem. ](*,) (on the other hand it is just as dangerous)[/QUOTE]

---

