---
title: "[SOLVED] Can I recover this partition"
date: 2008-08-15
forum: General Help
---

### Post by noobuntu35 on 2008-08-15
Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50bf50bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16417   131869521    7  HPFS/NTFS
/dev/sda2           16418       18241    14651280    5  Extended
/dev/sda5           16418       18158    13984551   83  Linux
/dev/sda6           18159       18241      666666   82  Linux swap / Solaris

Disk /dev/sdc: 2013 MB, 2013265920 bytes
129 heads, 32 sectors/track, 952 cylinders
Units = cylinders of 4128 * 512 = 2113536 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         953     1966064    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(960, 128, 32) logical=(952, 71, 32)

Disk /dev/sdd: 2055 MB, 2055208960 bytes
16 heads, 32 sectors/track, 7840 cylinders
this is the print out from sudo fdisk -l /dev/sda1 is what appears to be the Windows XP partition.
/dev/sda1   *           1       16417   131869521    7  HPFS/NTFS
/dev/sda2           16418       18241    14651280    5  Extended
however when I did the install of Ubuntu I some how killed the MBR with the Windows Recovery Console fixmbr command was devastating. I can not see the Files from Ubuntu, nor do I have a boot option. Am I right in thinking the OS is still there? many photo's too important to lose. Is there an easy fix? or am I looking at expensive recovery software I used  sudo nano /etc/fstab
and added this line  /dev/sda1 /windows ntfs nls=utf8,umask=0222 0 0 Yes I backed up etc/fstab first 
sudo umount /dev/sda1 says its not mounted, Good? 
 sudo mount -a
results in this
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
john@ubuntu:~$

---

### Post by iaculallad on 2008-08-15
[Photorec]("http://www.cgsecurity.org/wiki/PhotoRec") might be the right tool in your situation. You might also want to try [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by az on 2008-08-15
You can try to repair the NTFS boot sector.  See here:

[http://ubuntu-rescue-remix.org/node/57](http://ubuntu-rescue-remix.org/node/57)

If that fails, I would stop fiddling and move to file-carving, as mentioned, to recover your files.  Avoid writing to the drive until you got your data back.

[http://ubuntu-rescue-remix.org/forum](http://ubuntu-rescue-remix.org/forum)
[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)

---

### Post by noobuntu35 on 2008-08-15
> **iaculallad said:**
> [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec") might be the right tool in your situation. You might also want to try [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").

I am still learning how and where do I execute the programs?

---

### Post by iaculallad on 2008-08-15
> **noobuntu35 said:**
> I am still learning how and where do I execute the programs?

On your terminal:

```
sudo apt-get install testdisk
```

and how to make it work, read the [documentation]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") on their website.

---

### Post by noobuntu35 on 2008-08-15
> **iaculallad said:**
> On your terminal:

```
sudo apt-get install testdisk
```

and how to make it work, read the [documentation]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") on their website.

running it now... will reply back

---

### Post by noobuntu35 on 2008-08-15
you guys rock, the partitions are there, this may just be what I needed If not there is always the computer geeks at the local shop, and another backup drive

---

### Post by noobuntu35 on 2008-08-16
ok it was a long way around, after wrecking the Ubuntu install I was able to boot back to Windoze I used the program you 2 recommended and was able to rebuild my dual boot that and the recovery console from the Windoze XP disk. fixboot command 
now to get both up and working correctly, best part... Pictures are still here

---

### Post by noobuntu35 on 2008-08-18
dual boot running hehe, converted the whole family to Ubuntu users... They're happy to have the pics back. guess I now have a new gaming console... WINXP haha

---

### Post by NoVista on 2008-08-18
For any future booboo's, I always keep SuperGrub on hand.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by noobuntu35 on 2008-08-18
cool thanks I put it on a thumb drive, I may need that...

---

### Post by noobuntu35 on 2008-08-18
Disk /dev/sda - 150 GB / 139 GiB - CHS 18242 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1 16416 254 63  263739042<---- any one?
D HPFS - NTFS              0   1  1 18239 254 63  293025537<---- huh?
D Linux                 4505   2  1  6207 254 63   27358569
D Linux                16417   2  1 18157 254 63   27969039
D Linux                18156   1  1 18157 254 63      32067
D Linux Swap           18158   1  1 18240 254 63    1333332

ok so new problem same drive, why 2? XP is corrupted still oh wait thats redundant...

---

### Post by unutbu on 2008-08-18
Please post the output of 
```

sudo fdisk -l
```

---

### Post by noobuntu35 on 2008-08-18
Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a7978

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16417   131869521    7  HPFS/NTFS
/dev/sda2           16418       18241    14651280    5  Extended
/dev/sda5           18159       18241      666666   82  Linux swap / Solaris
/dev/sda6           16418       18158    13984519+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 2013 MB, 2013265920 bytes
129 heads, 32 sectors/track, 952 cylinders
Units = cylinders of 4128 * 512 = 2113536 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         953     1966064    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(960, 128, 32) logical=(952, 71, 32)

Disk /dev/sdd: 2055 MB, 2055208960 bytes
16 heads, 32 sectors/track, 7840 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x7e73e9db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        7840     2007024    b  W95 FAT32

---

### Post by noobuntu35 on 2008-08-18
isk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a7978

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16417   131869521    7  HPFS/NTFS
/dev/sda2           16418       18241    14651280    5  Extended
/dev/sda5           18159       18241      666666   82  Linux swap / Solaris
/dev/sda6           16418       18158    13984519+  83  Linux

took out thumb drives

---

### Post by unutbu on 2008-08-18
From the output of fdisk, your partition table looks ok. What program were you using that gave the strange output?

---

### Post by noobuntu35 on 2008-08-18
testdisk which is what initially recovered XP however even after a repair install doesnot quite work right cant update and Internet explorer doesn't work, not a real big deal but a few things I need it for, other thanthat it is going to be the new gamer console... I have converted the family :)
I'm waiting for it to finish running again I'll post each screen

---

### Post by noobuntu35 on 2008-08-19
Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1 16416 254 63  263739042
 2 E extended             16417   0  1 18240 254 63   29302560
   X extended             16417   0  2 18157 254 63   27969164
 6 L Linux                16417   2  1 18157 254 63   27969039
 5 L Linux Swap           18158   1  1 18240 254 63    1333332
this is interesting 
Boot sector                        Backup boot sector
0180 ebf2c30d 0a412064   .....A d  ebf2c30d 0a412064   .....A d
0188 69736b20 72656164   isk read  69736b20 72656164   isk read
0190 20657272 6f72206f    error o  20657272 6f72206f    error o
0198 63637572 72656400   ccurred.  63637572 72656400   ccurred.
01A0 0d0a4e54 4c445220   ..NTLDR   0d0a4e54 4c445220   ..NTLDR
01A8 6973206d 69737369   is missi  6973206d 69737369   is missi
01B0 6e67000d 0a4e544c   ng...NTL  6e67000d 0a4e544c   ng...NTL
01B8 44522069 7320636f   DR is co  44522069 7320636f   DR is co
01C0 6d707265 73736564   mpressed  6d707265 73736564   mpressed
01C8 000d0a50 72657373   ...Press  000d0a50 72657373   ...Press
01D0 20437472 6c2b416c    Ctrl+Al  20437472 6c2b416c    Ctrl+Al
01D8 742b4465 6c20746f   t+Del to  742b4465 6c20746f   t+Del to
01E0 20726573 74617274    restart  20726573 74617274    restart
01E8 0d0a0000 00000000   ........  0d0a0000 00000000   ........
this is from the boot record dump

---

### Post by noobuntu35 on 2008-08-20
well this one is officially closed, put in a second harddrive to do a back up, wasn't paying much attention to My IDE cable and # of connectors and location, HDD wouldn't work where I needed it and I was out of time to find another IDE cable. so I pulled the Hard drive back out.as an after thought "I cant use no need for it to be there" ended up dropping the HDD sleeve with both drives in it on the floor from about 3 1/2 feet drive is thrashed, booted at first, then started ticking slightly. Ubuntu log on screen was as far as I got... had to reboot, no HDD listed and No readable partitions harddrive is running but a slight tick,tick,tick so somethings wrong there. so much for saving lots of money :(

---

