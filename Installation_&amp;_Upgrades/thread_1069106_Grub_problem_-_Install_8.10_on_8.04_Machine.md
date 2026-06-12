---
title: "Grub problem - Install 8.10 on 8.04 Machine"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by pizzipie on 2009-02-13
Hi

I run a DEll Latitude D 800 w/ 160 GB hard drive. Dual boot with Windows XP and Ubuntu 8.04.1.

I installed Ubuntu 8.10 on top of this and now get the ERROR: Grubloading stage1.5 Grubloading, please wait ... Error 18. The attached file is the result file from boot_info_script024.sh.

Please help me sort ths out.

Rp

---

### Post by caljohnsmith on 2009-02-13
You have an interesting case of a Grub error 18, because it looks like it is not due to the usual cause; usually a Grub error 18 is a result of having an older BIOS that can't access anything on the HDD past either 8.4 GB or 137 GB. Therefore, if your Ubuntu's boot files are outside of the range your BIOS can access, Grub returns an error 18. But in your case, your Hardy boot files are located at about 42 GB, and your Intrepid boot files are at about 77 GB. So if you were able to boot Hardy OK without getting a Grub error 18, you should be able to boot Intrepid without getting a Grub error 18. A few months ago we saw a case exactly like this where the solution was to convert the Ubuntu partition from a logical partition into a primary partition. If you want to give that a try, it only means changing your partition table--you don't have to reinstall anything. And fortunately you still have one primary partition available, and also your partitions are physically arranged so that it should be easy to convert your sda9 Intrepid partition into a primary partition. So if that sounds OK with you, how about posting:
```
sudo sfdisk -d
```
Also, I notice you have two swap partitions, and you can actually share a swap partition between your two Ubuntu installs. So if you want, we could also delete the extra swap partition and you can use that extra space for your sda9 Intrepid partition or your sda5 partition. Let me know if that sounds OK with you.

---

### Post by pizzipie on 2009-02-13
Thanks for prompt reply caljohnsmith.

I am currently using the Intrepid live disk.

See  what Code: produced below:

 I am not too sure as to what to do now. The partitions I have sda5-7 can be sacrificed as I used them for possible re-booting of past Ubuntu OS's. I have never moved contents of partitions around.
I have newest Gparted and newest System rescuecd and therefore tools to work with. I have ISO images of Ubuntu8.04.02 as well as Feisty Gutsy etc and Windows XP. So, if you are willing to guide me, lets 'get er done'

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 78124032, Id= b, bootable
/dev/sda2 : start= 78124095, size= 16964640, Id=83
/dev/sda3 : start= 95088735, size=217487970, Id= 5
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=156248253, size= 48821472, Id=83
/dev/sda6 : start=205069788, size= 48821472, Id=83
/dev/sda7 : start=253891323, size= 48821472, Id=83
/dev/sda8 : start=302712858, size=  9863847, Id=82
/dev/sda9 : start= 95088861, size= 58540734, Id=83
/dev/sda10: start=153629658, size=  2618532, Id=82
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=  1959867, Id= b
/dev/sdb2 : start=  1959930, size= 13719510, Id=83
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0

---

### Post by caljohnsmith on 2009-02-13
Before we change your partition table around, what are you planning on doing with your sda2 8.04 install? Also, what is on sda5, sda6, and sda7?

---

### Post by pizzipie on 2009-02-13
sda5, sda6, and sda7 can be sacrificed. I need to keep Hardy8.04.1 as a bootable option if possible. I just need one partition where I can place any of the old editions of Ubuntu.

---

### Post by caljohnsmith on 2009-02-14
I had another idea that is really easy to try and just might work, so how about trying this first:
```
sudo grub
grub> root (hd0,8)
grub> install /boot/grub/stage1 (hd0) /boot/grub/stage2 p /boot/grub/menu.lst
```
That installs Grub to the MBR, yet it omits installing the Grub stage1.5 file so that Grub points directly to the stage2 file instead. After doing the above commands, reboot and let me know what happens on start up. We can work from there.

---

### Post by pizzipie on 2009-02-14
What I got was ... "grub> -"  It put me in the grub shell.

---

### Post by caljohnsmith on 2009-02-14
OK, since that didn't work, how about downloading the attached "partition_table.txt" file to your Ubuntu desktop (can be the Live CD or your install), and then do:
```
sudo sfdisk --no-reread -f /dev/sda -O ~/Desktop/sda_sectors_modified.save < ~/Desktop/partition_table.txt
```
And please post the output. The above command will create a backup of the few sectors being modified as a small "sda_sectors_modified.save" file on your desktop, so if for some reason anything were to go wrong, we can easily restore your original partition table with that file. Therefore, please copy that file to a different drive, or you could for instance save it to your email account or something like that. Next reboot your Live CD, and then do:
```
sudo fdisk -lu
sudo sfdisk -d
sudo grub
grub> root (hd0,2)
grub> setup (hd0)
grub> quit
```
Please post the output of all the above commands before typing "quit". Next reboot to your HDD and let me know how far you get. We can work from there.

---

### Post by pizzipie on 2009-02-14
Partition_table.txt CODE RESULTS:

Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   4862    4863-  39062016    b  W95 FAT32
/dev/sda2       4863    5918    1056    8482320   83  Linux
/dev/sda3       5919+   9562    3644-  29270367   83  Linux
/dev/sda4       9563   19457-   9895-  79476106+   5  Extended
/dev/sda5       9563+   9725     163-   1309266   82  Linux swap / Solaris
/dev/sda6       9726+  12764    3039-  24410736   83  Linux
/dev/sda7      12765+  15803    3039-  24410736   83  Linux
/dev/sda8      15804+  18842    3039-  24410736   83  Linux
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  78124094   78124032   b  W95 FAT32
/dev/sda2      78124095  95088734   16964640  83  Linux
/dev/sda3      95088861 153629594   58540734  83  Linux
/dev/sda4     153629595 312581807  158952213   5  Extended
/dev/sda5     153629658 156248189    2618532  82  Linux swap / Solaris
/dev/sda6     156248253 205069724   48821472  83  Linux
/dev/sda7     205069788 253891259   48821472  83  Linux
/dev/sda8     253891323 302712794   48821472  83  Linux
Successfully wrote the new partition table

Re-reading the partition table ...


 WARNINGS & ERRORS

Warning: given size (158952213) exceeds max allowable size (158947110)
Warning: partition 4 extends past end of disk
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs
If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

---

### Post by pizzipie on 2009-02-14
DISK-GRUB-CODE 




Code Results: sudo fdisk -lu
--------------------------------------------

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000cb898

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    78124094    39062016    b  W95 FAT32
/dev/sda2        78124095    95088734     8482320   83  Linux
/dev/sda3        95088861   153629594    29270367   83  Linux
/dev/sda4       153629595   312581807    79476106+   5  Extended
/dev/sda5       153629658   156248189     1309266   82  Linux swap / Solaris
/dev/sda6       156248253   205069724    24410736   83  Linux
/dev/sda7       205069788   253891259    24410736   83  Linux
/dev/sda8       253891323   302712794    24410736   83  Linux

Disk /dev/sdb: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders, total 15682559 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00032edb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     1959929      979933+   b  W95 FAT32
/dev/sdb2         1959930    15679439     6859755   83  Linux

################### No Errors reported ###############################

Code Results: sudo sfdisk -d
-----------------------------------------

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 78124032, Id= b, bootable
/dev/sda2 : start= 78124095, size= 16964640, Id=83
/dev/sda3 : start= 95088861, size= 58540734, Id=83
/dev/sda4 : start=153629595, size=158952213, Id= 5
/dev/sda5 : start=153629658, size=  2618532, Id=82
/dev/sda6 : start=156248253, size= 48821472, Id=83
/dev/sda7 : start=205069788, size= 48821472, Id=83
/dev/sda8 : start=253891323, size= 48821472, Id=83
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=  1959867, Id= b
/dev/sdb2 : start=  1959930, size= 13719510, Id=83
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0

################### No Errors reported ###############################

Code Results: sudo grub 
----------------------------------

grub>

################### No Errors reported ###############################


Code Results: grub> root (hd0,2)
---------------------------------------

ERROR 22 No such partition

######################################################################


Code Results: grub> setup (hd0)
---------------------------------------

ERROR 22 Invalid device requested

---

### Post by caljohnsmith on 2009-02-14
OK, so you made sure you rebooted to the Live CD after running the sfdisk command, true? If so, how about posting:
```
sudo parted /dev/sda print
sudo grub
grub> geometry (hd0)
grub> geometry (hd1)
grub> quit
```
And we can work from there.

---

### Post by pizzipie on 2009-02-14
when I re-booted I ended up in the grub shell  => grub>

Do you think I should re-do the whole partition table (except for windows as I'm leery of the ISO image I have)?

I am willing to keep going here though. I certainly will learn something. I really appreciate the time you are taking to help me and your patience.

Thank you caljohnsmith!!!!!

R

---

### Post by caljohnsmith on 2009-02-14
> **pizzipie said:**
> when I re-booted I ended up in the grub shell  => grub>

Do you think I should re-do the whole partition table (except for windows as I'm leery of the ISO image I have)?

I am willing to keep going here though. I certainly will learn something. I really appreciate the time you are taking to help me and your patience.

Thank you caljohnsmith!!!!!

R
You're welcome, I think we are making good progress. :) In your post #10, did you do those commands from your **Ubuntu Live CD** (the Ubuntu install CD), or did you do them while you were in your Ubuntu install on the HDD? You need to do them from your Live CD at this point. Please don't change your partition table, because the results you posted so far show it is just fine. So if you haven't done those commands from the Live CD, please do them and post the results; or if you did do them from the Live CD, when you reboot and get the Grub prompt, try:
```
grub> root (hd0,2)
grub> setup (hd0)
grub> reboot
```
And let me know how that goes.

---

### Post by pizzipie on 2009-02-17
I have to back up a bit as I got out of sync when Ubuntu did maintenance for a day and I was away for a day. So...back to # 11

attachement is Code for sudo parted /dev/sda print

############### Code for grub> geometry (hd0)  #################

drive 0x80 C/H/S 19457/255/63 No. Sectors 312581808 /dev/sda

partition        fs               type
0                   fat             0xb
1                   ext2fs         0x83
2                   ext2fs         0x83
4                   unknown    0x83
5                   ext2fs         0x83
6                    ext2fs        0x83
7                    ext2fs        0x83

############### Code for grub> geometry (hd1)  #################

drive 0x81 C/H/S 976/255/63 No. Sectors 15682559 /dev/sdb

partition        fs               type
0                   fat             0xb
1                   ext2fs         0x83

---

### Post by pizzipie on 2009-02-17
In answer to your #13 In booting from live disk and doing commands: grub> root did not show anythig ( good ) eh ?
grub>  setup (hd0) showed  success at stage 1, 1.5 and 2 ( good ) eh ?

As a side question, I can't re-direct code in grub to a file. Is this the way it is or do I have something wrong?? ie grub> setuo (hd0) >> fdisk-lu.txt doesn't work! nor does grub> setup (hd0) | cat >> fdisk-lu

---

### Post by caljohnsmith on 2009-02-17
That's good, after you rebooted you could finally run the Grub commands and get them to complete successfully. How about rebooting your HDD now and let me know exactly what happens.

---

### Post by pizzipie on 2009-02-17
SUCCESS !! it worked!! Thanks a million.

However, This is like being hit by a truck and waking up in the hospital not remembering anything.

What did you do to make it work. I only have a vague idea.

Now, can I dump some partitions or combine some ( sda5,6,7) for instance and install hardy in the freed up space?

Again thanks.

---

### Post by caljohnsmith on 2009-02-17
> **pizzipie said:**
> SUCCESS !! it worked!! Thanks a million.

However, This is like being hit by a truck and waking up in the hospital not remembering anything.

What did you do to make it work. I only have a vague idea.

Now, can I dump some partitions or combine some ( sda5,6,7) for instance and install hardy in the freed up space?

Again thanks.
That's great news it worked OK. All we did was convert your sda9 Ubuntu logical partition into the sda3 primary partition in your HDD's partition table. I've found from others' experience that converting the Ubuntu partition from a logical to primary partition can be a way to solve really arcane/illogical Grub error 18 problems, so fortunately it worked for you too. And yes, you can do whatever you want with sda5, sda6, and sda7 now that the partition table change is done and the dust has cleared. Cheers and enjoy your Ubuntu install. :)

---

### Post by pizzipie on 2009-02-18
THANK YOU AGAIN caljohnsmith.

Rick P

---

