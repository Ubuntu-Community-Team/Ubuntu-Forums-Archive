---
title: "Restore Grub"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by Vrekk on 2009-03-28
Recently I had a windows melt down on my dual boot so I had to reinstall windows.  Windows overwrote the MBR, which was expteced.  How ever when I folowed the instuctions from [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351") , i get an error message saying this ```
grub> setup (hd0) 
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested

```
Any ideas?

---

### Post by combatwombat_nz on 2009-03-28
Check out this thread:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
It explains reinstalling Grub from a live cd.

---

### Post by Vrekk on 2009-03-28
> **combatwombat_nz said:**
> Check out this thread:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
It explains reinstalling Grub from a live cd.

"How ever when I folowed the instuctions from [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) , i get an error message"

Might want to re-read my message there

---

### Post by meierfra. on 2009-03-28
Sounds like your partition table is slightly corrupt.  Boot from the LiveCD and post the output of

```
sudo fdisk -lu
sudo sfdisk -d

```

---

### Post by Vrekk on 2009-03-29
```
ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7d8c7d8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     2104514     1052226   82  Linux swap / Solaris
/dev/sda2         2104515    10120949     4008217+  83  Linux
/dev/sda3        10120950   976751999   483315525    f  W95 Ext'd (LBA)
/dev/sda4   *   488119023   976751999   244316488+   7  HPFS/NTFS
/dev/sda5        10121076   475973819   232926372   83  Linux
/dev/sda6       475973883   488118959     6072538+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=  2104452, Id=82
/dev/sda2 : start=  2104515, size=  8016435, Id=83
/dev/sda3 : start= 10120950, size=966631050, Id= f
/dev/sda4 : start=488119023, size=488632977, Id= 7, bootable
/dev/sda5 : start= 10121076, size=465852744, Id=83
/dev/sda6 : start=475973883, size= 12145077, Id=82
ubuntu@ubuntu:~$ 

```

---

### Post by meierfra. on 2009-03-29
> empty partition (5)

That's your problem.  To fix it, boot from the LiveCD,  download the attached file "PT.txt" to your Desktop and open a terminal. Rewrite your partition table via

```


sudo sfdisk -f --no-reread  -O ~/Desktop/OldPT.save /dev/sda < ~/Desktop/PT.txt
```

Post the output of that commmand.
Just as a precaution, copy the file OldPT.save to a save place outside your hard drive (Flashdrive,  online storage..) 

You should now be able to reinstall grub:

```
sudo grub
root (hd0,4)
setup (hd0)
quit
```

Reboot and you should  get  the Grub menu.

If "setup (hd0)" gave you an error message, reboot to the LiveCD and  try reinstalling grub again.
If after rebooting "setup (hd0)" still gives you an error messages post the output of that  "setup (hd0)" command and also the output of

```
sudo fdisk -lu
sudo sfdisk -d
sudo parted /dev/sda print
```

---

### Post by Vrekk on 2009-03-29
> **meierfra. said:**
> That's your problem.  To fix it, boot from the LiveCD,  download the attached file "PT.txt" to your Desktop and open a terminal. Rewrite your partition table via

```


sudo sfdisk -f --no-read  -O ~/Desktop/OldPT.save /dev/sda < ~/Desktop/PT.txt
```

Post the output of that commmand.


```
ubuntu@ubuntu:~$ sudo sfdisk -f --no-read  -O ~/Desktop/OldPT.save /dev/sda < ~/Desktop/PT.txt
sfdisk: unrecognized option '--no-read'
sfdisk (util-linux-ng 2.14)Usage: sfdisk [options] device ...
device: something like /dev/hda or /dev/sda
useful options:
    -s [or --show-size]: list size of a partition
    -c [or --id]:        print or change partition Id
    -l [or --list]:      list partitions of each device
    -d [or --dump]:      idem, but in a format suitable for later input
    -i [or --increment]: number cylinders etc. from 1 instead of from 0
    -uS, -uB, -uC, -uM:  accept/report in units of sectors/blocks/cylinders/MB
    -T [or --list-types]:list the known partition types
    -D [or --DOS]:       for DOS-compatibility: waste a little space
    -R [or --re-read]:   make kernel reread partition table
    -N# :                change only the partition with number #
    -n :                 do not actually write to disk
    -O file :            save the sectors that will be overwritten to file
    -I file :            restore these sectors again
    -v [or --version]:   print version
    -? [or --help]:      print this message
dangerous options:
    -g [or --show-geometry]: print the kernel's idea of the geometry
    -G [or --show-pt-geometry]: print geometry guessed from the partition table
    -x [or --show-extended]: also list extended partitions on output
                             or expect descriptors for them on input
    -L  [or --Linux]:      do not complain about things irrelevant for Linux
    -q  [or --quiet]:      suppress warning messages
    You can override the detected geometry using:
    -C# [or --cylinders #]:set the number of cylinders to use
    -H# [or --heads #]:    set the number of heads to use
    -S# [or --sectors #]:  set the number of sectors to use
You can disable all consistency checking with:
    -f  [or --force]:      do what I say, even if it is stupid
ubuntu@ubuntu:~$ 

```

---

### Post by meierfra. on 2009-03-29
May  bad.  it should say "--no-reread" in the first command. (I fixed my post)

---

### Post by Vrekk on 2009-03-29
Though it might be a simple typo, im just not smart enough to figure out what is was. Here is the new output
```
ubuntu@ubuntu:~$ sudo sfdisk -f --no-reread  -O ~/Desktop/OldPT.save /dev/sda < ~/Desktop/PT.txt

Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+    130     131-   1052226   82  Linux swap / Solaris
/dev/sda2        131     629     499    4008217+  83  Linux
/dev/sda3        630   60799   60170  483315525    f  W95 Ext'd (LBA)
/dev/sda4   *  30384+  60799   30416- 244316488+   7  HPFS/NTFS
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda5        630+  29627   28998- 232926372   83  Linux
/dev/sda6      29628+  30383     756-   6072538+  82  Linux swap / Solaris
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1            63   2104514    2104452  82  Linux swap / Solaris
/dev/sda2       2104515  10120949    8016435  83  Linux
/dev/sda3      10120950 488118959  477998010   f  W95 Ext'd (LBA)
/dev/sda4   * 488119023 976751999  488632977   7  HPFS/NTFS
/dev/sda5      10121076 475973819  465852744  83  Linux
/dev/sda6     475973883 488118959   12145077  82  Linux swap / Solaris
Warning: partition 4 does not start at a cylinder boundary
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
ubuntu@ubuntu:~$ 


```

---

### Post by meierfra. on 2009-03-29
That looks good. So follow the rest of the instruction, that is: reinstall grub.

---

### Post by Vrekk on 2009-03-29
Ok now Grub is installed and I can boot into ubuntu, I cant ;however, boot into Xp. I get error 13.  Also i get an error about a file system check failed when i boot into ubuntu. It says that the check failed then leaves me with a root terminal.  I can only get a GUI if i type reboot in the root terminal it gives me.

---

### Post by meierfra. on 2009-03-29
> I can boot into ubuntu,
Great.  Did reinstalling grub work the first time or did you had to reboot first?


> boot into Xp. I get error 13 i think? 


Sounds like, you need to edit menu.lst. Open a terminal in Ubuntu and  open the file menu.lst  via

```
gksudo gedit /boot/grub/menu.lst
```

and change  your windows item to

title Windows XP
rootnoverify  (hd0,3)
chainloader +1

Save the file and reboot.


**If this did not let you boot into XP:  **

In order to get a clearer picture of your setup, I suggest to boot into  Ubuntu  and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Vrekk on 2009-03-29
> **meierfra. said:**
> Great.  Did reinstalling grub work the first time or did you had to reboot first? 
First Time


So now xp starts up just fine, but i get an error booting ubutnu about a failed file system check. It saved a log that i attached.  Then i get a root termnail (root@brett-desktop:~# ) There i have to type in reboot in order to get to a GUI.

---

### Post by meierfra. on 2009-03-29
Sounds like /etc/fstab needs to be edited. Post the output of

```
cat /etc/fstab
```

and 

```
 sudo blkid -c /dev/null
```

---

### Post by Vrekk on 2009-03-29
```
brett@brett-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=d89990a7-2081-49ad-b5d5-b02b8f2604a1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=a3d52c7e-4aca-413b-82e0-bdc30393de91 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda3   /media/sda3   ext3   defaults   0   2
/dev/sda5   /media/sda5   ntfs-3g   defaults,locale=en_US.UTF-8  0  0
brett@brett-desktop:~$  sudo blkid -c /dev/null
[sudo] password for brett: 
Sorry, try again.
[sudo] password for brett: 
/dev/sda1: UUID="8f2e69c4-bc45-4343-83d0-fb847ef35a41" TYPE="swap" 
/dev/sda2: UUID="506fb74e-fb38-4418-aaf1-c04fd0eb16e5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="9AC4BF54C4BF30FD" TYPE="ntfs" 
/dev/sda5: UUID="d89990a7-2081-49ad-b5d5-b02b8f2604a1" TYPE="ext3" 
/dev/sda6: UUID="a3d52c7e-4aca-413b-82e0-bdc30393de91" TYPE="swap" 
brett@brett-desktop:~$ 

```

---

### Post by Vrekk on 2009-03-29
Yes i got it! I edited the /ect/fstab and removed 
```
/dev/sda3   /media/sda3   ext3   defaults   0   2
```
line and changed 
```
/dev/sda5   /media/sda5   ntfs-3g   defaults,locale=en_US.UTF-8  0  0

```
to
```
/dev/sda4   /media/Xp   ntfs-3g   defaults,locale=en_US.UTF-8  0  0

```
now my system is back to the way i had it before!
Thanks for everthing!

---

### Post by meierfra. on 2009-03-29
> Yes i got it.
Great.


> I removed
```
 /dev/sda3  /media/sda3   ext3   defaults   0   2
```


What is on /dev/sda2?  (your 4GB ext3  partition). If you want to mount it automatically, rename /media/sda3 via

```
sudo mv /media/sda3 /media/sda2
```

and at 

```
 /dev/sda2  /media/sda2   ext3   defaults   0   2
```

to fstab.

> 
Thanks for everthing! 
You are welcome. Have fun with XP and Ubuntu.

---

