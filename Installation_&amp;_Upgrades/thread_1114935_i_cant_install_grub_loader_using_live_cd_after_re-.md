---
title: "i cant install grub loader using live cd after re-installing windows xp"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by xihad76 on 2009-04-03
while trying to re-install grub according to the instruction stated [here]("http://ubuntuforums.org/showthread.php?t=224351") i found the following messages:

```
grub> root (hd0,5)
grub> setup (hd0)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 16 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed
Error 12: Invalid device requested

```

## here are the output of the codes suggested by Meierfra: 

```
ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 40.0 GB, 40019582464 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78163247 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xab3fab3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    14329979     7164958+   7  HPFS/NTFS
/dev/sda2        14329980    78140159    31905090    f  W95 Ext'd (LBA)
/dev/sda3        28660023    45046259     8193118+   b  W95 FAT32
/dev/sda5        14330106    25655804     5662849+  83  Linux
/dev/sda6        25655868    28659959     1502046   82  Linux swap / Solaris
/dev/sda7        45046323    61432559     8193118+   b  W95 FAT32
/dev/sda8        61432623    78140159     8353768+   b  W95 FAT32


ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 14329917, Id= 7, bootable
/dev/sda2 : start= 14329980, size= 63810180, Id= f
/dev/sda3 : start= 28660023, size= 16386237, Id= b
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 14330106, size= 11325699, Id=83
/dev/sda6 : start= 25655868, size=  3004092, Id=82
/dev/sda7 : start= 45046323, size= 16386237, Id= b
/dev/sda8 : start= 61432623, size= 16707537, Id= b


```
so can anyone plz help me? thnx in advance...

---

### Post by meierfra. on 2009-04-03
> empty partition (5)
That's your problem. To fix it, boot from the LiveCD, download the attached file "PT.txt" to your Desktop and open a terminal. Rewrite your partition table via


```

sudo sfdisk -f --no-reread  -O ~/Desktop/OldPT.save /dev/sda < ~/Desktop/PT.txt
```

Post the output of that commmand.
Just as a precaution, copy the file OldPT.save to a save place outside your hard drive (Flashdrive, online storage..)

You should now be able to reinstall grub:


```
sudo grub
root (hd0,4)
setup (hd0)
quit
```

Post the output of that "setup (hd0)" command and also the output of

```
sudo fdisk -lu
sudo sfdisk -d
sudo parted /dev/sda print
```

Reboot and you should get the Grub menu.

---

### Post by ajgreeny on 2009-04-03
hd0,5 is your swap so there is no point using that in the root command.  It should be root (hd0,4).  You forgot grub starts from 0 (zero), not 1.
EDIT:  Drat, too slow.

---

### Post by meierfra. on 2009-04-03
> You forgot grub starts from 0 (zero), not 1.

I don't thing so. The OP just used the output of "find /boot/grub/stage1"

The "omitted empty partition(5)" message from "fdisk" means that there is a bogus entry in the partition table.  Ubuntu just ignores this entry and does not assigns a device name to that bogus partition. But grub actually counts that partition and thinks that Ubuntu is on (hd0,5). Of course this leads to confusion and installing grub fails.  So one needs to fix the partition table.  One can use "testdisk" to fix the partition table, but personally I find "sfdisk" more convenient.

---

### Post by xihad76 on 2009-04-03
```
buntu@ubuntu:~$ sudo sfdisk -f --no-reread  -O ~/Desktop/OldPT.save /dev/sda < ~/Desktop/PT.txt

Disk /dev/sda: 4865 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+    891     892-   7164958+   7  HPFS/NTFS
/dev/sda2        892    4863    3972   31905090    f  W95 Ext'd (LBA)
/dev/sda3       1784+   2803    1020-   8193118+   b  W95 FAT32
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5        892+   1596     705-   5662849+  83  Linux
/dev/sda6       1597+   1783     187-   1502046   82  Linux swap / Solaris
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda7       2804+   3823    1020-   8193118+   b  W95 FAT32
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda8       3824+   4863    1040-   8353768+   b  W95 FAT32
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
New situation:
Units = sectors of 512 bytes, counting from 0

Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  14329979   14329917   7  HPFS/NTFS
/dev/sda2      14329980  78140159   63810180   f  W95 Ext'd (LBA)
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5      14330106  25655804   11325699  83  Linux
/dev/sda6      25655868  28659959    3004092  82  Linux swap / Solaris
/dev/sda7      28660023  45046259   16386237   b  W95 FAT32
/dev/sda8      45046323  61432559   16386237   b  W95 FAT32
/dev/sda9      61432623  78140159   16707537   b  W95 FAT32
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs
If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)


```

```
grub> root (hd0,4)
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,4)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

```

These are the two outputs.

---

### Post by meierfra. on 2009-04-03
Looks good. So you should be able to boot into Ubuntu on reboot.

---

### Post by xihad76 on 2009-04-03
here r the other three::

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40019582464 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78163247 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xab3fab3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    14329979     7164958+   7  HPFS/NTFS
/dev/sda2        14329980    78140159    31905090    f  W95 Ext'd (LBA)
/dev/sda5        14330106    25655804     5662849+  83  Linux
/dev/sda6        25655868    28659959     1502046   82  Linux swap / Solaris
/dev/sda7        28660023    45046259     8193118+   b  W95 FAT32
/dev/sda8        45046323    61432559     8193118+   b  W95 FAT32
/dev/sda9        61432623    78140159     8353768+   b  W95 FAT32





ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 14329917, Id= 7, bootable
/dev/sda2 : start= 14329980, size= 63810180, Id= f
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 14330106, size= 11325699, Id=83
/dev/sda6 : start= 25655868, size=  3004092, Id=82
/dev/sda7 : start= 28660023, size= 16386237, Id= b
/dev/sda8 : start= 45046323, size= 16386237, Id= b
/dev/sda9 : start= 61432623, size= 16707537, Id= b


ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA SAMSUNG SP0411N (scsi)
Disk /dev/sda: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  7337MB  7337MB  primary   ntfs         boot 
 2      7337MB  40.0GB  32.7GB  extended               lba  
 5      7337MB  13.1GB  5799MB  logical   ext3              
 6      13.1GB  14.7GB  1538MB  logical   linux-swap        
 7      14.7GB  23.1GB  8390MB  logical   fat32             
 8      23.1GB  31.5GB  8390MB  logical   fat32             
 9      31.5GB  40.0GB  8554MB  logical   fat32  
```

---

### Post by xihad76 on 2009-04-03
Still not working.. 

this time the grub loader appears. but after cliking this is displayed :

error 15: file not found.. 

:(

---

### Post by meierfra. on 2009-04-03
Well, you are making progress.

Try this:

At the grub menu at boot up, select ubuntu, but do press "enter". press "e" instead. At the new menu press "e" again.

replace the whole text by

root (hd0,4)

Press "enter" and then "b" to boot.


**If this did boot you into Ubuntu**

Open a terminal in Ubuntu and open the file "menu.lst" via


```
gksudo gedit /boot/grub/menu.lst
```

Look for the line

# groot=(hd?,?)   
(or # groot=some_long_string)

Change it to

# groot=(hd0,4)


Save the file. Back in the terminal

```
sudo update-grub
```


**If this did NOT boot you into Ubuntu**

Boot from the Ubuntu LiveCD and download the Boot Info Script to your desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and type:


> sudo bash ~/Desktop/boot_info_script*.sh

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post (use the code tags) The results of that script will help clarify your setup.

---

### Post by xihad76 on 2009-04-03
yep. this time it worked! i m writing this reply rite from my good old UBUNTU :D 

both in Grub loader and menu.list the root was set to (hd0,7)...
and i have updated the menu.list as u suggested above.. 

Dear Meierfra, thnk u very  much mate.. u have been so helpful... if i were living in ur place i would surely buy u a drink :-)  

would u mind if i ask u which part of the world u r from?

thnx again... take care..

---

### Post by meierfra. on 2009-04-03
> if i ask u that u r from which part of the world...

I'm a German living in the USA.


> i m writing this reply rite from my good old UBUNTU

Great.   Are you able to boot into Windows as well?

---

### Post by xihad76 on 2009-04-03
> **meierfra. said:**
>  Are you able to boot into Windows as well?

yeah. just checked it. this is also working fine.. 

> I'm a German living in the USA.

great to know that. there is a good chance for me to go to Germany for my masters prog. next yr. 


thnx again buddy. take care..

---

### Post by miden on 2009-04-19
Hi all. I too was having this problem and I did all of the above (except rebooting). However when I get to the ens to do the setup (hd0) I get this...

grub> root (hd0,4)

grub> setup (hd0)

Error 17: Cannot mount selected partition

grub> 

I get the same result running it as (hd0,5) as well......Any ideas?

Dennis

---

### Post by meierfra. on 2009-04-19
miden: Please don't  post in two different  threads  on the same subject. 
Anyway, I see what is  causing your problems and I will post in your other thread. Just give me a minute.

---

### Post by miden on 2009-04-19
sorry.. I got confused as to which thread it should be in...The other guy stopped replying so I thought I was in teh wrong one..Also I think you said it was a more a Tips thread so I thought OOPS, my bad wrong one...

The I saw this and saw it was EXACTLY the same problem so in view of teh above I decided to proceed on this one. Sorry.

Should I delete the other thread?

Dennis

---

### Post by meierfra. on 2009-04-19
> The other guy stopped replying so I thought I was in teh wrong one.

Don't be so impatient. He  just responded  with the perfect solution, so there is no more reason for me to get involved.

---

### Post by miden on 2009-04-19
With all due respect, I was NOT being impatient. And the last reply in that thread was NOT by the guy I was talking about...That was someone else much earlier.

I thought the first responder stopped because I was in the wrong thread. After all, he replied twice within 20 minutes so I thought he was up with the pace, so to speak. But then he stopped responding so I thought it was my fault because I was in the wrong thread. 

Impatience never came into it! Is everyone on these forums so touchy!! 
I managed to get this far with Ubuntu and Ubuntu Studio and was happily running a dual boot system, without asking any questions, and the first time I post I cop this??? I made a simple mistake and you jump up on your soapbox.

---

