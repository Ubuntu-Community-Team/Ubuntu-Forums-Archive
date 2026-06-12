---
title: "Partition table overlaps, possibly due to Super Grub Disk"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by Forlornity on 2009-02-17
Hey all, I'm having some troubles with parted.
It tells me I have overlapping partitions.

I recently installed Windows XP on a small 20GB partition outside of the extended partition in which my Ubuntu partitions reside, then I restored GRUB to the MBR using Super Grub Disk, This worked fine, Ubuntu booted without issue. I'd intended to shrink my Ubuntu partition and grow my windows one (20GB isn't enough for a full XP install along with all of the half life series :P)
I went to open gparted, but it died with the error "Cannot have overlapping partitions", I tried with parted, same error.
Here's the output of fdisk -lu
```
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1f29c9cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    14465023     7231488   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2        14469840   270632879   128081520    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3        78457680   270632879    96087600   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4   *   270632880   312575759    20971440    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5        14469966    73059839    29294937   83  Linux
/dev/sda6        73059903    78457679     2698888+  82  Linux swap / Solaris

```

and windows displays my partition table as such:
[ATTACH]103621[/ATTACH]

I can boot both windows and ubuntu fine at the moment, but I'd really like to be able to resize my partitions and I feel uncomfortable with my partition table in such a state.
Many thanks in advance, Forlornity.

---

### Post by caljohnsmith on 2009-02-17
> **Forlornity said:**
> 
```
[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1f29c9cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    14465023     7231488   27  Unknown
Partition 1 does not end on cylinder boundary.
[COLOR="Red"]/dev/sda2        14469840   270632879[/COLOR]   128081520    5  Extended
Partition 2 does not end on cylinder boundary.
[COLOR="Red"]/dev/sda3        78457680   270632879[/COLOR]    96087600   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4   *   270632880   312575759    20971440    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5        14469966    73059839    29294937   83  Linux
/dev/sda6        73059903    78457679     2698888+  82  Linux swap / Solaris

```

Unfortunately your partition table is corrupt, because as parted has all ready alerted you, your sda HDD has overlapping partitions. Or to be more specific, your sda3 primary partition is inside of your sda2 extended partition, so sda3 should be a logical partition instead. If you would like some help fixing your partition table, how about posting:
```
sudo sfdisk -d
```
Also, which partition has your main Ubuntu install, sda3 or sda5?

---

### Post by Forlornity on 2009-02-17
sudo sfdisk -d:
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size= 14462976, Id=27
/dev/sda2 : start= 14469840, size=256163040, Id= 5
/dev/sda3 : start= 78457680, size=192175200, Id=83
/dev/sda4 : start=270632880, size= 41942880, Id= 7, bootable
/dev/sda5 : start= 14469966, size= 58589874, Id=83
/dev/sda6 : start= 73059903, size=  5397777, Id=82

```

My main install was on two partitions inside the extended partition (or should be at least, that's how it was after install) with / being on sda5 and /home on sda3.
Here's df -h:
```
/dev/sda5              28G  5.7G   21G  22% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  364K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.8M 1009M   1% /dev
tmpfs                1012M  104K 1012M   1% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda3              91G   62G   24G  72% /home

```

---

### Post by caljohnsmith on 2009-02-17
Do you have a Live CD that you can boot? You will need that in order to carry out all the steps, because you will need to reinstall Grub to the MBR since we have to make your sda3 partition sda5, and then your sda5 partition will become sda6. So if you have a Live CD ready, how about downloading the attached "partition_table.txt" file to your Ubuntu desktop (at this point it can be your Ubuntu install on sda5 or the Live CD, it doesn't matter), and then do:
```
sudo sfdisk --no-reread -f /dev/sda < ~/Desktop/partition_table.txt
```
And please post the output. Then reboot to your Live CD, and please post the output of all the following commands:
```
sudo fdisk -lu
sudo parted /dev/sda print
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
And we can work from there.

---

### Post by Forlornity on 2009-02-17
So do I run ```
sudo sfdisk --no-reread -f /dev/sda < ~/Desktop/partition_table.txt
``` in the liveCD or booted?
Or does it not matter?

Just gotta be sure :)

---

### Post by caljohnsmith on 2009-02-17
> **Forlornity said:**
> So do I run ```
/media/Data/dotnetfx3setup.exe
``` in the liveCD or booted?
Or does it not matter?

Just gotta be sure :)
Where did you get that command? That's not the sfdisk command I gave in my post. You can run that sfdisk from your booted Ubuntu install or the Live CD, it does not matter so long as you first download the "partition_table.txt" file to your desktop. You might as well run it from your Ubuntu install since that is where you seem to be right now.

---

### Post by Forlornity on 2009-02-17
Output for partition table rewrite:
```
Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+    900-    901-   7231488   27  Unknown
		end: (c,h,s) expected (900,103,35) found (956,163,35)
/dev/sda2        900+  16846-  15946- 128081520    5  Extended
		start: (c,h,s) expected (900,180,1) found (957,0,1)
		end: (c,h,s) expected (1023,254,63) found (1023,239,63)
/dev/sda3       4883+  16846-  11963-  96087600   83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
		end: (c,h,s) expected (1023,254,63) found (1023,239,63)
/dev/sda4   *  16846+  19456-   2611-  20971440    7  HPFS/NTFS
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
		end: (c,h,s) expected (1023,254,63) found (1023,239,63)
/dev/sda5        900+   4547-   3648-  29294937   83  Linux
		start: (c,h,s) expected (900,182,1) found (957,2,1)
		end: (c,h,s) expected (1023,254,63) found (1023,239,63)
/dev/sda6       4547+   4883-    336-   2698888+  82  Linux swap / Solaris
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
		end: (c,h,s) expected (1023,254,63) found (1023,239,63)
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1          2048  14465023   14462976  27  Unknown
/dev/sda2      14469840 270632879  256163040   5  Extended
/dev/sda3             0         -          0   0  Empty
/dev/sda4   * 270632880 312575759   41942880   7  HPFS/NTFS
/dev/sda5      78457680 270632879  192175200  83  Linux
/dev/sda6      14469966  73059839   58589874  83  Linux
/dev/sda7      73059903  78457679    5397777  82  Linux swap / Solaris
Warning: partition 1 does not end at a cylinder boundary
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

```

Ran that in main booted env.
Rebooting to liveCD now.

---

### Post by Forlornity on 2009-02-17
> **caljohnsmith said:**
> Where did you get that command? That's not the sfdisk command I gave in my post. You can run that sfdisk from your booted Ubuntu install or the Live CD, it does not matter so long as you first download the "partition_table.txt" file to your desktop. You might as well run it from your Ubuntu install since that is where you seem to be right now.

My mistake, had the correct command copied then I went and middle clicked :P
I meant the sfdisk command.

Also, for note, I'm posting this on my desktop, while my laptop's the one with the issues, and it's all backed up so no need to worry too much, though I'd rather not have to go through the restoration process again, of course.

And thanks for the help so far :)

---

### Post by Forlornity on 2009-02-17
Here's the output of my liveCD session:
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1f29c9cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    14465023     7231488   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2        14469840   270632879   128081520    5  Extended
/dev/sda4   *   270632880   312575759    20971440    7  HPFS/NTFS
/dev/sda5        78457680   270632879    96087600   83  Linux
/dev/sda6        14469966    73059839    29294937   83  Linux
/dev/sda7        73059903    78457679     2698888+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA HITACHI HTS54251 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  7406MB  7405MB  primary   ntfs              
 2      7409MB  139GB   131GB   extended                    
 6      7409MB  37.4GB  30.0GB  logical   ext3              
 7      37.4GB  40.2GB  2764MB  logical   linux-swap        
 5      40.2GB  139GB   98.4GB  logical   ext3              
 4      139GB   160GB   21.5GB  primary   ntfs         boot 

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$ 


```

and during the grub session:

```
grub> root (hd0,5)

grub> setup (hd0) 
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.


```

Any more before I reboot?

- Forlornity

---

### Post by caljohnsmith on 2009-02-17
I forgot to ask, but are you using 8.10 or a previous Ubuntu version? If you are using 8.10, go ahead and reboot and let me know how far you get. If you are using a version prior to 8.10, you will probably have to tweak your menu.lst to account for the new partition changes. Let me know if that applies to you or not.

---

### Post by Forlornity on 2009-02-17
Intrepid, yes.
Booting now, looks promising.
I'll test it out then tell you :)

Thanks much for the help.

---

### Post by Forlornity on 2009-02-17
Ubuntu's booting fine, XP's lost its hal.dll, but I should be able to replace that fairly swiftly, all the partitions mount fine and all looks good, thanks a lot!
:)

---

### Post by caljohnsmith on 2009-02-17
You're welcome, glad you can boot into Ubuntu now at least. About getting a "missing hal.dll" error when booting Windows, I think you will find that Windows isn't missing that file; since we changed your partition table, your Windows boot.ini file is misconfigured now. If you want help correcting that, how about doing:
```
sudo mount /dev/sda4 /mnt
gksudo gedit /mnt/boot.ini
```
And then change the two instances of "partition(3)" to "partition(2)" instead like:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition[COLOR="Blue"](2)[/COLOR]\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition[COLOR="Blue"](2)[/COLOR]\WINDOWS="Microsoft Windows XP" /fastdetect /NoExecute=OptIn
```
Then try booting Windows, and if all goes well it should work OK now. Let me know how that goes or if you run into problems.

---

### Post by Forlornity on 2009-02-18
It was what I was doing anyway :P
Once I'd noticed the change in my partition table at least.

Thanks very much for your help, I would've been tearing my hair for a day or so 'til I figured it out otherwise :)

- Forlornity

---

### Post by ebf.beltran on 2010-10-09
I have a similar problem.

I resized my partitions with Partition Manager in order to grant Ubuntu with more space and I get two things:
```
1)
      At start up I get:

grub rescue>
grub rescue>ls
(hd0) (hd0,1) (hd0,2) (hd0,3) ... (hd0,5)

I am not sure how far it goes I think it also included hd0,6

and 

2)
     Using a CD to but Ubuntu I get from sudo fdisk -l:

Device Boot      Start            End            Blocks           ID              System
/dev/sda1          1                     192           1536000       27           Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2          192           12442          98403341        7             HPFS/NTFS
/dev/sda3        12443       14594          17279987        5               Extended
/dev/sda5        12443       14550          16932478        83             Linux
/dev/sda6        14551       14594          345088            82             Linux swap / Solaris

```
So I was wondering if you think my problem could be resolved by fixing the partition table or if the problem is probably bigger.

---

### Post by srs5694 on 2010-10-10
ebf.beltran, first, please see [my Web page on this symptom.](http://www.rodsbooks.com/missing-parts/) My suspicion is that you've got this problem.

Second, if you need more help, please post the *complete* output of "sudo fdisk -lu" (note the "u"), and please post it between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings to improve legibility.

---

### Post by ebf.beltran on 2010-10-11
I read the site and thank you. I had already tried most of what was there before replying. I don't like asking questions that have already been answered but I am a bit stock since I had never before manipulated partitions... a bit back when I used Windows 3.1 but it was a long time ago.

I don't really need to fix the computer, but rather access a few files in the partition that are part of my research. I don't mind starting from scratch afterwards. Is just that half of the data was not backed up.

When I mount the windows part I can access without problem from the Ubuntu CD but when I mount the linux partition I get:

```

Unable to mount location

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Well here are the specifics I got

```

root@ubuntu:/home/ubuntu# fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6bba44a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2         3074048   199880729    98403341    7  HPFS/NTFS
/dev/sda3   *   199880730   234440703    17279987    5  Extended
/dev/sda5       199880793   233745749    16932478+  83  Linux
/dev/sda6       233750528   234440703      345088   82  Linux swap / Solaris


```I also bashed a set of data from another thread that looks like this

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: /dev/sda5: can't read superblock

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2           3,074,048   199,880,729   196,806,682   7 HPFS/NTFS
/dev/sda3    *    199,880,730   234,440,703    34,559,974   5 Extended
/dev/sda5         199,880,793   233,745,749    33,864,957  83 Linux
/dev/sda6         233,750,528   234,440,703       690,176  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        84A4EC25A4EC1C04                       ntfs       TOSHIBA SYSTEM VOLUME         
/dev/sda2        F4D6F105D6F0C93E                       ntfs       Windows                       
/dev/sda3: PTTYPE="dos" 
/dev/sda5        08e48988-0d05-41e0-8ce7-d106041c43fb   ext4                                     
/dev/sda6        c5bc2b4c-70b2-4bf9-b75b-f96cbdba5175   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)



```

---

### Post by srs5694 on 2010-10-11
I don't think it's a partitioning problem; your partitions look fine to me, so unless I've missed something or there's an issue too subtle to show up in the fdisk output, it's not partitions.

Your Boot Info Script output, however, does include a clue:

```

mount: /dev/sda5: can't read superblock

```

This suggests that something has damaged the filesystem on /dev/sda5. Given that the problems began when you resized it (expanding it earlier on the disk, I presume), it's possible that it's been very badly damaged. If possible, I recommend you do a dd backup of the partition to another disk before you do anything else; that way, you can try fairly aggressive recovery procedures and restore to the current condition if you think they may have damaged the disk further. If that's not possible, I suppose you'll just have to forge ahead. I'd try fsck first, and if that doesn't work, delete the partition using fdisk and then use TestDisk; maybe it will be able to do something with it. If that fails, you may just have to re-install, perhaps using PhotoRec to recover any user files that are important to you. (That will be a tough task, though.)

Good luck!

---

### Post by ebf.beltran on 2010-10-11
So I have space in an external hard drive how can I use dd to copy the partition of interest in terms of the research data???


Already into it... sorry for asking.

---

### Post by ebf.beltran on 2010-10-12
PhotoRec did the job

I already have the data I had lost. THANK U!

I was wondering if you could point me in the right direction to at least making Windows work again if you think that is at all possible.

If you think it is a lot of work I might just go on and reformat and reinstall.

---

### Post by srs5694 on 2010-10-12
You could try re-installing GRUB, or you could install a standard DOS/Windows-style boot loader in the MBR. You might look at [ms-sys-free](http://sourceforge.net/projects/ms-sys-free/) for the latter.

---

