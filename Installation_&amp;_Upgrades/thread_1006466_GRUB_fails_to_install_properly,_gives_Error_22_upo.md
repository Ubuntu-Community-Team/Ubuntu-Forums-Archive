---
title: "GRUB fails to install properly, gives Error 22 upon boot"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by BuggyBY on 2008-12-09
Hello everyone.

Having just installed Intrepid Ibex after some false starts, I am having some trouble getting GRUB to boot from the correct partitions. I have previously described the problem in [the University of Sheffield Free Software Society forum (recommend you read the whole sad story)]("http://www.fss.union.shef.ac.uk/forum/viewtopic.php?t=258"), but I will do my best to summarise the issue below:

At first, grub-install failed to start at all. This seems to have been because my desired Ubuntu boot partition was logical instead of primary, and has since been amended by letting a proprietary partition manager work its magic to turn the logical partition primary.

Then, a fresh reformat and reinstallation of the entire ubuntu system (I like to go for overkill when it comes to installation errors) finished without any error, and the PC rebooted to display nothing but:

[INDENT]GRUB Loading stage1.5



GRUB loading, please wait...
Error 22[/INDENT]

I restarted from the Ubuntu Live CD and edited the install partition's GRUB menu.lst to point to the correct partitions only, but the same error remains accusingly on my screen whenever I boot from hard disk.

The regulars at fss.union.shef.ac.uk (the aforementioned student society's forum) suggested I ask for help here as well, and with some delay, this is what I am now doing.

---

### Post by caljohnsmith on 2008-12-09
Ubuntu can boot just fine from a logical partition or primary partition, so that shouldn't be your problem. How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. Note "-l" is a lowercase L, not a one. And finally, for each command above that returns "eb48", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "eb48". That will greatly clarify what your setup is like.

---

### Post by BuggyBY on 2008-12-09
Here's the full terminal output:

```
 ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa94750a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    15824024     7911981    b  W95 FAT32
/dev/sda2        15824025   284896709   134536342+   f  W95 Ext'd (LBA)
/dev/sda5        15824088   284029199   134102556    b  W95 FAT32

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0970ca77

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    11839904     5919921    b  W95 FAT32
/dev/sdb2        11839905   390716864   189438480    f  W95 Ext'd (LBA)
/dev/sdb5        11839968   114238214    51199123+   7  HPFS/NTFS
/dev/sdb6       114238278   257602274    71681998+   7  HPFS/NTFS
/dev/sdb7       257602338   390716864    66557263+   7  HPFS/NTFS

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe0ebe0eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    21719879    10859908+   c  W95 FAT32 (LBA)
/dev/sdc2        21719880   586099394   282189757+   f  W95 Ext'd (LBA)
/dev/sdc5        21719943   226532564   102406311    c  W95 FAT32 (LBA)
/dev/sdc6       226532628   523188854   148328113+   c  W95 FAT32 (LBA)
/dev/sdc7       523188918   580862204    28836643+  83  Linux
/dev/sdc8       580862268   586099394     2618563+  82  Linux swap / Solaris
omitting empty partition (5)

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa42a1187

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   512000495   256000216+   7  HPFS/NTFS
/dev/sdd2       512000496  1024000991   256000248    7  HPFS/NTFS
/dev/sdd3      1876801311  1953525167    38361928+  83  Linux
/dev/sdd4      1024002000  1876801310   426399655+   f  W95 Ext'd (LBA)
/dev/sdd5      1024002063  1459280591   217639264+   7  HPFS/NTFS
/dev/sdd6      1459280655  1876801247   208760296+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sde: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              38     7839719     3919841    b  W95 FAT32
ubuntu@ubuntu:~$ sudo xxd -l 2 -p /dev/sda
eb31
ubuntu@ubuntu:~$ sudo xxd -l 2 -p /dev/sdb
33c0
ubuntu@ubuntu:~$ sudo xxd -l 2 -p /dev/sdc
eb48
ubuntu@ubuntu:~$ sudo xxd -l 2 -p /dev/sdd
33c0
ubuntu@ubuntu:~$ sudo xxd -l 2 -p /dev/sde
0000
ubuntu@ubuntu:~$ sudo xxd -s 1049 -l 2 -p /dev/sdc
0281
```
Hope this helps. I wonder why sdb3 is missing from the partition list - as far as I know it's my installation's root partition.

---

### Post by caljohnsmith on 2008-12-09
OK, that clears a few things up; Grub is installed to the MBR (Master Boot Record) of your sdc drive, and it points to the 2nd boot drive and 3rd partition for its boot files, which is supposed to be your sdd drive it looks like. But your sdd drive is probably not the 2nd boot drive on start up, so that would explain why you are getting the Grub error 22. You have linux partitions though on both your sdc and sdd drives; do you know which has the main Ubuntu file system? I'm guessing your main Ubuntu install is on sdd3. But then what is on sdc7? 

In order to help find out, please post the output of:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
grub> quit
```
And more importantly, if your main Ubuntu partition is on the sdd drive, can you change your BIOS to boot the sdd drive on start up instead of the sdc drive? That will greatly simplify fixing your booting problem, and it would be the most ideal solution I think since your drives would then not be dependent on each other for booting.

---

### Post by BuggyBY on 2008-12-09
sdc7 is probably my /home partition. I've changed sdd to be the first hard drive (apparently it was the fifth), but only got a "Reboot and Select proper Boot device" error. I changed the boot device to a third hard drive on a whim, and suddenly the BIOS stopped recognising any more than two hard drives! I changed back to the original boot device, and now GRUB gives me Error 17, which the manual tells me stands for "Cannot mount selected partition - This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB."

Very odd.

---

### Post by BuggyBY on 2008-12-09
Also, now the Ubuntu Live CD does not boot properly anymore, instead giving the following output:
```
Loading, please wait...



BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [    73.396023] ata4: SRST failed (errno=-16)
[    78.424021] ata4: SRST failed (errno=-16)
[    78.424059] ata4: reset failed, giving up

```
I'm now left with a shell I am not sure what I'm supposed to do with. Upon reboot a similar message is displayed, replacing ata4 with ata8. On yet another reboot it changed back to ata4. It seems to oscillate back and forth between the two with every reboot.

Very odd.

---

### Post by caljohnsmith on 2008-12-09
It sounds like you might have accidentally changed something else in your BIOS in addition to modifying the boot order. You might try resetting the BIOS setting back to default if you can't find what is causing the problem. Once you can get the Live CD working again, you can do these steps to install Grub to the MBR of the sdd drive so that it will be bootable:
```
sudo grub
grub> root (hd3,2)
grub> setup (hd3)
grub> quit
```
And if you set your BIOS to boot the sdd drive, you should at least get a Grub menu on start up if all goes well. Let me know if your run into problems though.

---

