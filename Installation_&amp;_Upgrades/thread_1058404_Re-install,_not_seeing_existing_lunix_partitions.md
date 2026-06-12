---
title: "Re-install, not seeing existing lunix partitions"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by beekr on 2009-02-02
I'm trying to reinstall 8.1, but when it comes to the section for partitions, my existing partitions are not showing on the screen. My only two options are for full hdd usage and manual; what happened to the third option. I select manual and it shows nothing. when I run the ' fdisk -lu' command, it list my linux partitions and none of them are hidden. Is there a trick to getting them to show or do I need to nuke them and start over?

Thanks
Beekr

"I'll block your entire subnet you LAMERS! . . . .I am ROOT!"

---

### Post by caljohnsmith on 2009-02-02
How about opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
sudo sfdisk -d
sudo parted -l
```
Please post the output, and we can work from there if you want.

---

### Post by beekr on 2009-02-02
ok here is the sudo fdisk -lu :

$ sudo fdisk -lu
[sudo] password for mike: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   483153920   488394751     2620416    c  W95 FAT32 (LBA)
/dev/sda2          178176    21149695    10485760    7  HPFS/NTFS
/dev/sda3   *    21149696   329269231   154059768    7  HPFS/NTFS
/dev/sda4       329284366   488394751    79555193    f  W95 Ext'd (LBA)
/dev/sda5       483153920   488394751     2620416   dd  Unknown
/dev/sda6       329284368   469483559    70099596   83  Linux
/dev/sda7       469483623   479235014     4875696   83  Linux
/dev/sda8       479235078   483138809     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

and here is the sudo sfdisk -d

$ sudo sfdisk -d
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=483153920, size=  5240832, Id= c, bootable
/dev/sda2 : start=   178176, size= 20971520, Id= 7
/dev/sda3 : start= 21149696, size=308119536, Id= 7, bootable
/dev/sda4 : start=329284366, size=159110386, Id= f
/dev/sda5 : start=483153920, size=  5240832, Id=dd
/dev/sda6 : start=329284368, size=140199192, Id=83
/dev/sda7 : start=469483623, size=  9751392, Id=83
/dev/sda8 : start=479235078, size=  3903732, Id=82

and last here is the sudo parted -l

$ sudo parted -l
Error: Can't have overlapping partitions.   

Thank you

---

### Post by caljohnsmith on 2009-02-02
> **beekr said:**
> ```

$ sudo fdisk -lu
[sudo] password for mike: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   [COLOR="Red"]483153920   488394751[/COLOR]     2620416    c  W95 FAT32 (LBA)
/dev/sda2          178176    21149695    10485760    7  HPFS/NTFS
/dev/sda3   *    21149696   329269231   154059768    7  HPFS/NTFS
/dev/sda4       [COLOR="Red"]329284366   488394751[/COLOR]    79555193    f  W95 Ext'd (LBA)
/dev/sda5       [COLOR="Red"]483153920   488394751[/COLOR]     2620416   dd  Unknown
/dev/sda6       329284368   469483559    70099596   83  Linux
/dev/sda7       469483623   479235014     4875696   83  Linux
/dev/sda8       479235078   483138809     1951866   82  Linux swap / Solaris

$ sudo parted -l
[COLOR="Red"]Error: Can't have overlapping partitions.[/COLOR] 
```  

Unfortunately as you can see from the parted error, and also as shown highlighted in red from the fdisk output, your sda1 partition overlaps with your sda4 extended partition. In fact, your sda1 partition and sda5 partition are right on top of each other (they are the same partition). Can you mount sda1? How about posting the output of:
```

sudo mount /dev/sda1 /mnt && ls -l /mnt

```
And we can work from there.

---

### Post by beekr on 2009-02-02
I was able to mount sda1 and I was also able to get a directory listing on all partitions except the swap. here is the output for the sfdisk:

$ sudo sfdisk -l
[sudo] password for mike: 

Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *  30074+  30401-    327-   2620416    c  W95 FAT32 (LBA)
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda2         11+   1316-   1306-  10485760    7  HPFS/NTFS
/dev/sda3   *   1316+  20496-  19180- 154059768    7  HPFS/NTFS
/dev/sda4      20497+  30401-   9905-  79555193    f  W95 Ext'd (LBA)
/dev/sda5      30074+  30401-    327-   2620416   dd  Unknown
/dev/sda6      20497+  29223    8727-  70099596   83  Linux
/dev/sda7      29224+  29830     607-   4875696   83  Linux
/dev/sda8      29831+  30073     243-   1951866   82  Linux swap / Solaris

---

### Post by caljohnsmith on 2009-02-02
OK, great, how about next running this command:
```
echo '0,0,0' | sudo sfdisk --no-reread -fuS /dev/sda -N1
```
Please post the output, then reboot, and post the new output of:
```

sudo blkid -c /dev/null /dev/sda5
sudo fdisk -lu
sudo parted -l
```
And we can work from there.

---

### Post by beekr on 2009-02-03
ok here we go. the echo command results:

$ echo '0,0,0' | sudo sfdisk --no-reread -fuS /dev/sda -N1
[sudo] password for mike: 

Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Old situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   * 483153920 488394751    5240832   c  W95 FAT32 (LBA)
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda2        178176  21149695   20971520   7  HPFS/NTFS
/dev/sda3   *  21149696 329269231  308119536   7  HPFS/NTFS
/dev/sda4     329284366 488394751  159110386   f  W95 Ext'd (LBA)
/dev/sda5     483153920 488394751    5240832  dd  Unknown
/dev/sda6     329284368 469483559  140199192  83  Linux
/dev/sda7     469483623 479235014    9751392  83  Linux
/dev/sda8     479235078 483138809    3903732  82  Linux swap / Solaris
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *         0         -          0   0  Empty
/dev/sda2        178176  21149695   20971520   7  HPFS/NTFS
/dev/sda3   *  21149696 329269231  308119536   7  HPFS/NTFS
/dev/sda4     329284366 488394751  159110386   f  W95 Ext'd (LBA)
/dev/sda5     483153920 488394751    5240832  dd  Unknown
/dev/sda6     329284368 469483559  140199192  83  Linux
/dev/sda7     469483623 479235014    9751392  83  Linux
/dev/sda8     479235078 483138809    3903732  82  Linux swap / Solaris
Warning: partition 1 has size 0 and is bootable
Warning: partition 4 extends past end of disk
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

[rebooted]

result for sudo blkid -c /dev/null /dev/sda5  :

$ sudo blkid -c /dev/null /dev/sda5
[sudo] password for mike: 
/dev/sda5: LABEL="MEDIADIRECT" UUID="CC37-B428" TYPE="vfat" 

result for sudo fdisk -lu   :
$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           0           0           0    0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sda2          178176    21149695    10485760    7  HPFS/NTFS
/dev/sda3   *    21149696   329269231   154059768    7  HPFS/NTFS
/dev/sda4       329284366   488394751    79555193    f  W95 Ext'd (LBA)
/dev/sda5       483153920   488394751     2620416   dd  Unknown
/dev/sda6       329284368   469483559    70099596   83  Linux
/dev/sda7       469483623   479235014     4875696   83  Linux
/dev/sda8       479235078   483138809     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

result for sudo parted -l  :
$ sudo parted -l
Model: ATA WDC WD2500BEVS-7 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 2      91.2MB  10.8GB  10.7GB  primary   ntfs              
 3      10.8GB  169GB   158GB   primary   ntfs         boot 
 4      169GB   250GB   81.5GB  extended               lba  
 6      169GB   240GB   71.8GB  logical   ext3              
 7      240GB   245GB   4993MB  logical   ext3              
 8      245GB   247GB   1999MB  logical   linux-swap        
 5      247GB   250GB   2683MB  logical   fat32  

/w00t no errors this time heh

---

### Post by caljohnsmith on 2009-02-03
Great, looks like you're in business now; your partition table looks just fine and parted didn't complain either. :) There's just a few small details to take care of, so please do the following:
```
sudo sfdisk -A3 /dev/sda
sudo sfdisk -c /dev/sda 5 c
```
Let me know if you run into any more problems, but you should be all set.

---

### Post by beekr on 2009-02-03
ok, I understand my partitions were hosed, but what in the world did we just do to fix it? After I post this, I'm going to try and reinstall. Thanks again for your help.

Beekr

---

### Post by caljohnsmith on 2009-02-03
Well the command in post #6 deleted your sda1 partition, and the first command in post #8 set the boot flag on your sda3 NTFS partition while removing the boot flag from the non-existent sda1 partition. The second command from post #8 changed the file system ID of your sda5 partition from "unknown" to FAT32 since that partition appears to be FAT32. Anyway, cheers and hope your new Ubuntu install goes smoothly. :)

---

### Post by beekr on 2009-02-03
Installed like a charm. Thanks a ton. You're a credit to the community. 

Beekr

---

### Post by caljohnsmith on 2009-02-03
I'm glad to hear your install went well, beekr; I realized though that I forgot to ask you, do you have Windows installed to sda2 or sda3? If so, I don't think you will be able to boot into Windows until we change a few things. Please let me know, and also please post the new output of:
```
sudo fdisk -lu
sudo sfdisk -d
```
And we can work from there if necessary.

---

### Post by beekr on 2009-02-03
Yeah I have windows vista installed; not sure what sda it is on. I was able to boot into it. I have one of those Dell XPS M1530s; one partition vista, one partition media direct and the other recovery. I can't get into media direct and haven't even tried recovery option. 

output for 'sudo fdisk -lu':
$ sudo fdisk -lu
[sudo] password for mike: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2          178176    21149695    10485760    7  HPFS/NTFS
/dev/sda3   *    21149696   329269231   154059768    7  HPFS/NTFS
/dev/sda4       329284366   488394751    79555193    f  W95 Ext'd (LBA)
/dev/sda5       483153920   488394751     2620416    c  W95 FAT32 (LBA)
/dev/sda6       329284368   469483559    70099596   83  Linux
/dev/sda7       469483623   479235014     4875696   83  Linux
/dev/sda8       479235078   483138809     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

output for 'sudo sfdisk -d' :
$ sudo sfdisk -d
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=        0, size=        0, Id= 0
/dev/sda2 : start=   178176, size= 20971520, Id= 7
/dev/sda3 : start= 21149696, size=308119536, Id= 7, bootable
/dev/sda4 : start=329284366, size=159110386, Id= f
/dev/sda5 : start=483153920, size=  5240832, Id= c
/dev/sda6 : start=329284368, size=140199192, Id=83
/dev/sda7 : start=469483623, size=  9751392, Id=83
/dev/sda8 : start=479235078, size=  3903732, Id=82

---

### Post by caljohnsmith on 2009-02-03
As long as you can boot Vista OK, I think you should be fine. Let me know if you run into any problems though.

---

### Post by beekr on 2009-02-03
I can't seem to boot into the media direct. Do I need to make the windows 95 partition active/ bootable? Thanks again

---

### Post by beekr on 2009-02-03
Gives me an error "Error 12: Invalid device request"

---

### Post by caljohnsmith on 2009-02-03
OK, I see now from the results in your post #7 that the FAT partition is actually your Media Direct partition, so instead of deleting sda1 and keeping sda5 like we did, we should have deleted sda5 and kept sda1 since the Media Direct partition should be a primary partition. I guess I should have asked you up front what was on all your partitions before deciding to let the FAT partition be logical partition sda5 rather than primary partition sda1; sorry about that. Anyway, it shouldn't be hard to change sda5 back into sda1, so how about downloading the attached "partition_table.txt" file to your Ubuntu desktop, and then do:
```
sudo sfdisk --no-reread -f /dev/sda -O ~/Desktop/sda_sectors_modified.save < ~/Desktop/partition_table.txt
```
And please post the output. The above command will create a backup of the few sectors being modified as a small "sda_sectors_modified.save" file on your desktop, so if for some reason anything were to go wrong, we can easily restore your original partition table with that file. Therefore, please copy that file to a different drive, or you could for instance save it to your email account or something like that. Also note that because we will be turning logical partition sda5 into primary partition sda1, all your other logical partitions will shift by one number: sda6 --> sda5, sda7 --> sda6, and sda8 --> sda7. Thus you will need to reinstall Grub so that Grub knows to use the new partition. But before doing that, after running the above command, be sure to reboot first to your Live CD, and please post the new output of:
```
sudo fdisk -lu
sudo parted -l
```
And if that output shows the correct changes, you can reinstall Grub with:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hd0,X) where X is a number, and (hd0,X) should be either (hd0,4) or (hd0,5), depending on whether Grub's boot files are on sda5 or sda6, respectively. Use that result as follows:
```

grub> root (hd0,X)
grub> setup (hd0)
grub> quit
```
If the above commands complete successfully, reboot, and let me know how far you get. We can work from there.

---

### Post by beekr on 2009-02-03
ok output for 'sudo fdisk -lu' :
$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x30000000

Device Boot Start End Blocks Id System
/dev/sda1 483153920 488394751 2620416 c W95 FAT32 (LBA)
/dev/sda2 178176 21149695 10485760 7 HPFS/NTFS
/dev/sda3 * 21149696 329269231 154059768 7 HPFS/NTFS
/dev/sda4 329284305 483138809 76927252+ f W95 Ext'd (LBA)
/dev/sda5 329284368 469483559 70099596 83 Linux
/dev/sda6 469483623 479235014 4875696 83 Linux
/dev/sda7 479235078 483138809 1951866 82 Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by caljohnsmith on 2009-02-03
Great, looks like everything is OK. Also, if you still want to get Media Direct booting again, how about trying:
```
sudo sfdisk -c /dev/sda 1 dd
```
Even though the Media Direct partition actually has a FAT32 file system, one of your original Media Direct partitions used "dd" for the file system ID. I think if we change the file system ID to "dd" then that might be what it takes to get it booting again. Let me know how that goes if you try it.

---

### Post by beekr on 2009-02-04
Same error 12.

---

### Post by caljohnsmith on 2009-02-04
Beekr, I must apologize, because even though I thought I remembered that a Media Direct partition should be a primary partition, I think that must be wrong. I did some more googling, and of the examples I found of other people who have a Media Direct partition, their Media Direct partition is always the first logical partition, i.e. sda5. So I'm thinking we had it right to begin with when your Media Direct partition was a logical partition; the thing I did wrong was to have you change the file system ID from "dd" to "c" which is a FAT32 partition (and the partition really is FAT32, but that probably confuses your Media Direct software since it is probably still looking for "dd"). Anyway, if you want to switch your sda1 partition back to sda5, let me know and we can do that. You'll of course have to reinstall Grub to the MBR again, but as you all ready know that's not a big deal.

---

### Post by beekr on 2009-02-18
Sorry for my late reply. Yeah! lets make the change. Thanks again.

---

### Post by caljohnsmith on 2009-02-19
OK, let's change the Media Direct partition back to sda5. :) How about downloading the attached "partition_table.txt" file to your Ubuntu desktop, and then do:
```
sudo sfdisk --no-reread -f /dev/sda -O ~/Desktop/sda_sectors_modified.save < ~/Desktop/partition_table.txt
```
And please post the output. As like last time, please save the "sda_sectors_modified.save" file on your desktop to some other drive or to some online account. After that, reboot to your Live CD and post the output of the commands from post #17 starting with the fdisk command. You'll also want to run the Grub commands to reinstall Grub. Let me know how that goes or if you run into problems.

---

### Post by beekr on 2009-02-21
Ok, here is the output of first command:

<code>
sudo sfdisk --no-reread -f /dev/sda -O  ~/Desktop/sda_sectors_modified.save < ~/Desktop/partition_table.txt

Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1      30074+  30401-    327-   2620416   dd  Unknown
/dev/sda2         11+   1316-   1306-  10485760    7  HPFS/NTFS
/dev/sda3   *   1316+  20496-  19180- 154059768    7  HPFS/NTFS
/dev/sda4      20497   30073    9577   76927252+   f  W95 Ext'd (LBA)
/dev/sda5      20497+  29223    8727-  70099596   83  Linux
/dev/sda6      29224+  29830     607-   4875696   83  Linux
/dev/sda7      29831+  30073     243-   1951866   82  Linux swap / Solaris
Warning: given size (5240832) exceeds max allowable size (0)
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1        178176  21149695   20971520   7  HPFS/NTFS
/dev/sda2   *  21149696 329269231  308119536   7  HPFS/NTFS
/dev/sda3             0         -          0   0  Empty
/dev/sda4     329284305 483138809  153854505   f  W95 Ext'd (LBA)
/dev/sda5     483153920 488394751    5240832  dd  Unknown
/dev/sda6     329284368 469483559  140199192  83  Linux
/dev/sda7     469483623 479235014    9751392  83  Linux
/dev/sda8     479235078 483138809    3903732  82  Linux swap / Solaris
Warning: partition 5 is not contained in partition 4
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
</code>

Does this look good to move on to next steps/commands as in post#17 ?

---

### Post by caljohnsmith on 2009-02-21
My mistake, it looks like I forgot to change the ending sector of the sda4 extended partition to accommodate the new sda5 MediaDirect partition. To correct it, how about doing:
```
echo "329284305,159110447,f" | sudo sfdisk --no-reread -fuS /dev/sda -N4
```
Please post the output, and then go ahead and do the rest of the commands from post #17. We can work from there.

---

### Post by beekr on 2009-02-21
echo "329284305,159110447,f" | sudo sfdisk --no-reread -fuS /dev/sda -N4
[sudo] password for mike: 

Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1        178176  21149695   20971520   7  HPFS/NTFS
/dev/sda2   *  21149696 329269231  308119536   7  HPFS/NTFS
/dev/sda3             0         -          0   0  Empty
/dev/sda4     329284305 483138809  153854505   f  W95 Ext'd (LBA)
/dev/sda5     483153920 488394751    5240832  dd  Unknown
/dev/sda6     329284368 469483559  140199192  83  Linux
/dev/sda7     469483623 479235014    9751392  83  Linux
/dev/sda8     479235078 483138809    3903732  82  Linux swap / Solaris
Warning: given size (159110447) exceeds max allowable size (159107760)
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1        178176  21149695   20971520   7  HPFS/NTFS
/dev/sda2   *  21149696 329269231  308119536   7  HPFS/NTFS
/dev/sda3             0         -          0   0  Empty
/dev/sda4     329284305 488394751  159110447   f  W95 Ext'd (LBA)
/dev/sda5     483153920 488394751    5240832  dd  Unknown
/dev/sda6     329284368 469483559  140199192  83  Linux
/dev/sda7     469483623 479235014    9751392  83  Linux
/dev/sda8     479235078 483138809    3903732  82  Linux swap / Solaris
Warning: partition 4 extends past end of disk
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

ok, going to start post #17 commands. Will pause to let you look over.

---

### Post by beekr on 2009-02-21
My bad, I pasted output, but didn't save and rebooted. I can boot into ubuntu, but not vista or media direct. What do you want me to do now? Thanks again

---

### Post by caljohnsmith on 2009-02-21
OK, to boot Vista, how about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change the Vista entry to use (hd0,1). Let me know if that works OK or not to boot Vista. Also, please post the output of:
```
sudo fdisk -lu
sudo parted /dev/sda print
```
Just so I can make sure you partition table is OK now. About using your Media Direct partition, I don't know what else we can do, because it is back to being the sda5 partition and also has "dd" for its file system like it should. What kind of error do you get when trying to use it?

---

### Post by beekr on 2009-02-21
heh think I found it. hold on:

sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1          178176    21149695    10485760    7  HPFS/NTFS
/dev/sda2   *    21149696   329269231   154059768    7  HPFS/NTFS
/dev/sda4       329284305   488394751    79555223+   f  W95 Ext'd (LBA)
/dev/sda5       483153920   488394751     2620416   dd  Unknown
/dev/sda6       329284368   469483559    70099596   83  Linux
/dev/sda7       469483623   479235014     4875696   83  Linux
/dev/sda8       479235078   483138809     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD2500BEVS-7 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      91.2MB  10.8GB  10.7GB  primary   ntfs              
 2      10.8GB  169GB   158GB   primary   ntfs         boot 
 4      169GB   250GB   81.5GB  extended               lba  
 6      169GB   240GB   71.8GB  logical   ext3              
 7      240GB   245GB   4993MB  logical   ext3              
 8      245GB   247GB   1999MB  logical   linux-swap        
 5      247GB   250GB   2683MB  logical   fat32             


Warning: Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Error: /dev/scd0: unrecognised disk label                                 

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,5)
grub> root (hd0,5)
root (hd0,5)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit

---

### Post by beekr on 2009-02-21
Changing Vista to HD0,1 worked. I can boot to it now.

---

### Post by caljohnsmith on 2009-02-21
Glad to hear that Vista boots OK, but what exactly happens when you try to boot your Media Direct partition? What error do you get?

---

### Post by beekr on 2009-02-21
It gives an error "Error 12: Invalid device request"

---

### Post by caljohnsmith on 2009-02-22
> **beekr said:**
> It gives an error "Error 12: Invalid device request"
Actually what I meant is what happens when you try to boot your Media Direct partition using your Media Direct button (or whatever it was you used that worked originally)?

---

### Post by beekr on 2009-02-23
It gives that error. It gives me the Media Direct splash screen and then the error.

---

### Post by caljohnsmith on 2009-02-23
One last sanity check would be to make sure the sda5 partition is still mountable/readable:
```
sudo mount /dev/sda5 /mnt && ls -l /mnt
```
If that doesn't return an error and gives you a directory listing instead, I don't know what else we can do then to get your Media Direct partition to boot.

---

### Post by troegs on 2009-02-24
Sorry for the fly by posting. Didn't read the whole forum but sounds like you're having a similar problem as I did. Not sure if you're still stuck on the partition part of the install not seeing your correct drives but that's the problem I was having. found out that with some systems the "use largest free space" is bugged. It will show that it's overwriting your windows partition, but (for me at least) it wasn't. Took a bit of a leap of faith to hit that next button but worked just fine. windows still boots to the raging piece OS that it was built to be and ubuntu is running like a dream.. hope this helps.. 

And after a little digging I found a post in regards to what I'm talking about.. 

[https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/149832](https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/149832)

Again, sorry if I'm "out of my element" coming in to a conversation I only read part of but I thought it might help. GL

---

