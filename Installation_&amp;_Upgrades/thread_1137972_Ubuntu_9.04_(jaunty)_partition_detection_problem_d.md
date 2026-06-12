---
title: "Ubuntu 9.04 (jaunty) partition detection problem during installation"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by karth83 on 2009-04-26
I was using Ubuntu 7.10 on my DELL XPS 1530 laptop. It was dual boot with  Windows Vista. It has a Media Direct Drive(fat32) at the end.

I downloaded ubuntu 9.04 and started installing. It didn't detect my partitions correctly. 

[ATTACH]111101[/ATTACH]

I deleted the Linux partitions from windows and tried. still ubuntu not detecting drugin installation. Then I formatted the deleted partition into fat32, and still problem persists.

The same partition worked with Ununtu 7.10 installation. I dont know what is the problem now.

The output of the following i have attached.

sudo fdisk -lu

[ATTACH]111104[/ATTACH]

sudo sfdisk -d

[ATTACH]111105[/ATTACH]

and also
sda2 ntfs windows recovery drive
sda4 C: OS
sda5 D:
sda6: empty Fat32 (going to use linux in this)

attached the windows Disk Magament also.

[ATTACH]111106[/ATTACH]

---

### Post by meierfra. on 2009-04-26
The problem is that the primary partition /dev/sda4 sits inside the extended partition /dev/sda3.

To fix the partition table,  boot from the LiveCD, download the attached file "PT.txt" to your Desktop and open a terminal. Then

```

sudo sfdisk -f --no-reread  -O ~/Desktop/OldPT.save /dev/sda < ~/Desktop/PT.txt

```

Just as a precaution, post the output of that commmand and copy the file OldPT.save to a save place outside your hard drive (Flashdrive, online storage, email account,...)

---

### Post by karth83 on 2009-04-26
ok i will try that and post the output before installing

---

### Post by karth83 on 2009-04-26
Thank you for your efforts in making the txt for me :)

I understood that u have resized sda3. But I have a doubt in that. At the end of sda4, u have removed the bootable word just after id=c. Is that ok?

---

### Post by meierfra. on 2009-04-26
> At the end of sda4, u have removed the bootable word just after id=c. Is that ok?

Yes. You should have only one boot flag. (If you are lucky the second boot flag just gets ignored, but if you are unlucky it will prevent your system from  booting)

Edit:  I hope you did not change the file in any way.  Even just an extra blank line at the end will corrupt the file.

---

### Post by karth83 on 2009-04-26
> **meierfra. said:**
> Yes. You should have only one boot flag. (If you are lucky the second boot flag just gets ignored, but if you are unlucky it will prevent your system from  booting)

Edit:  I hope you did not change the file in any way.  Even an extra blank line at the end, will corrupt the file.

Yes. I have not changed the file. Let me try and post the output of rewriting the partition.

---

### Post by karth83 on 2009-04-26
> **karth83 said:**
> Yes. I have not changed the file. Let me try and post the output of rewriting the partition.

This is he output: What shall I do next Pls?

ubuntu@ubuntu:/media$ sudo sfdisk -f --no-reread  -O ~/Desktop/OldPT.save /dev/sda < ~/Desktop/PT.txt

Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1         10+   1315-   1306-  10485760    7  HPFS/NTFS
/dev/sda2   *   1315+   6537-   5222-  41943040    7  HPFS/NTFS
/dev/sda3       6537+  19457-  12920- 103778304+   f  W95 Ext'd (LBA)
/dev/sda4   *  19130+  19457-    327-   2620416    c  W95 FAT32 (LBA)
/dev/sda5       6537+  17856-  11319-  90917888    7  HPFS/NTFS
/dev/sda6      17856+  19130-   1275-  10238976    b  W95 FAT32
Warning: given size (5240832) exceeds max allowable size (5239489)
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1        161792  21133311   20971520   7  HPFS/NTFS
/dev/sda2   *  21133312 105019391   83886080   7  HPFS/NTFS
/dev/sda3     105021439 307337215  202315777   5  Extended
/dev/sda4     307337216 312578047    5240832   c  W95 FAT32 (LBA)
/dev/sda5     105021440 286857215  181835776   7  HPFS/NTFS
/dev/sda6     286859264 307337215   20477952   b  W95 FAT32
Warning: partition 4 extends past end of disk
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

---

### Post by meierfra. on 2009-04-26
The output looks good. So you should be all set. Or are you still having problems?

---

### Post by SourceV on 2009-04-26
Hi,

I have a similar problem. I wonder if you could you please help me fixing this frustrating problem.


Here is the output.

```

ronen@RonenLT:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7f20ebf6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+   7  HPFS/NTFS
/dev/sda2            1825       13833    96462292+   5  Extended
/dev/sda3           13834       14593     6104700    7  HPFS/NTFS
/dev/sda4           13460       13833     3004123+  82  Linux swap / Solaris
/dev/sda5            1825        3040     9767457   83  Linux
/dev/sda6            3041        8511    43945776   83  Linux
/dev/sda7            8512       13459    39744778+  83  Linux

Partition table entries are not in disk order
ronen@RonenLT:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7f20ebf6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    29302559    14651248+   7  HPFS/NTFS
/dev/sda2        29302560   222227144    96462292+   5  Extended
/dev/sda3       222227145   234436544     6104700    7  HPFS/NTFS
/dev/sda4       216218898   222227144     3004123+  82  Linux swap / Solaris
/dev/sda5        29302686    48837599     9767457   83  Linux
/dev/sda6        48837663   136729214    43945776   83  Linux
/dev/sda7       136729278   216218834    39744778+  83  Linux

Partition table entries are not in disk order
ronen@RonenLT:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 29302497, Id= 7, bootable
/dev/sda2 : start= 29302560, size=192924585, Id= 5
/dev/sda3 : start=222227145, size= 12209400, Id= 7
/dev/sda4 : start=216218898, size=  6008247, Id=82
/dev/sda5 : start= 29302686, size= 19534914, Id=83
/dev/sda6 : start= 48837663, size= 87891552, Id=83
/dev/sda7 : start=136729278, size= 79489557, Id=83
ronen@RonenLT:~$   

```


Thanks.

Please let me know if you need further information.

---

### Post by karth83 on 2009-04-26
> **meierfra. said:**
> The output looks good. So you should be all set. Or are you still having problems?

:( Actually got into some other problem. I restarted after the partition change. Windows booted well. Then I shut down my laptop. I accidently pressed my DELL MEDIA DIRECT Button on my laptop. (It is a seperate OS like thing, where we can see movies without booting into windows.  )

It booted and told my boot settings are wrong and asked me to put my DELL recovery cd and repair. I did it and the partitions became like old. The DELL MEDIA DIRECT partition which was moved out of extended partition, again become part of the extended. I doubt because of the MEDIA DIRECT option only I have 2 Bootable entries in my partition info. So in future if i accidently press the DELL MEDIA DIRECT Button, then the boot problems will occur again. I dont know what to do now. 
Actually Ubuntu 7.10 detected the MEDIA DIRECT as a seperate OS, I remember it now.  When there was no problem with ubuntu 7.10, why it should create problem now?

I have attached the Windows Disk Management

[ATTACH]111221[/ATTACH]

I think actually the New Volume of 9.76GB should be moved out of the Extended partition for Ubuntu to detect it. This new Volume was my old Ubuntu partition + swap. I deleted the partition and formatted into fat32.

---

### Post by meierfra. on 2009-04-26
**karth83:**
Just to make sure the partition table reverted to the old one, could  you post the output of 

```
sudo fdisk -lu
sudo sfdisk -d
```
again.  

Also could you use copy and paste, rather than posting a screen shot?
(To copy in a terminal use "Ctrl+Shift+C")

---

### Post by meierfra. on 2009-04-26
**SourceV: ** Could you start a new thread with your problem?  Trying to solve two  problems in one thread can get pretty confusing. Thanks.

---

### Post by SourceV on 2009-04-26
Sure.

Here it is: [http://ubuntuforums.org/showthread.php?t=1138565](http://ubuntuforums.org/showthread.php?t=1138565)

Thanks

---

### Post by karth83 on 2009-04-27
> **meierfra. said:**
> **karth83:**
Just to make sure the partition table reverted to the old one, could  you post the output of 

```
sudo fdisk -lu
sudo sfdisk -d
```
again.  

Also could you use copy and paste, rather than posting a screen shot?
(To copy in a terminal use "Ctrl+Shift+C")

ya sure. I am a beginner in linux and I was not knowing how to copy from terminal. Right now I am in work place. I will post the output once I reach home. Please wait :) and thank you very much for your support.
Posting shortly ...........

---

### Post by karth83 on 2009-04-27
sudo fdisk -lu:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x10000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   307337216   312578047     2620416    c  W95 FAT32 (LBA)
/dev/sda2          161792    21133311    10485760    7  HPFS/NTFS
/dev/sda3   *    21133312   105019391    41943040    7  HPFS/NTFS
/dev/sda4       105021439   312578047   103778304+   f  W95 Ext'd (LBA)
/dev/sda5       105021440   286857215    90917888    7  HPFS/NTFS
/dev/sda6       286859264   307337215    10238976    b  W95 FAT32

Partition table entries are not in disk order
```



sudo sfdisk -d:

```

ubuntu@ubuntu:~$ sudo sfdisk -d
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=307337216, size=  5240832, Id= c, bootable
/dev/sda2 : start=   161792, size= 20971520, Id= 7
/dev/sda3 : start= 21133312, size= 83886080, Id= 7, bootable
/dev/sda4 : start=105021439, size=207556609, Id= f
/dev/sda5 : start=105021440, size=181835776, Id= 7
/dev/sda6 : start=286859264, size= 20477952, Id= b
```

---

### Post by meierfra. on 2009-04-27
There is something weird going on. So in  order to get a clearer picture of your setup, could you boot  from the  Ubuntu Live CD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it.

---

### Post by karth83 on 2009-04-27
> **meierfra. said:**
> 


```
sudo bash ~/Desktop/boot_info_script*.sh
```




```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /bootmgr /BOOTMGR /boot/bcd 
                       /BOOT/bcd /Boot/bcd /boot/BCD /BOOT/BCD /Boot/BCD 
                       /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x10000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *    307,337,216   312,578,047     5,240,832   c W95 FAT32 (LBA)
/dev/sda2             161,792    21,133,311    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,133,312   105,019,391    83,886,080   7 HPFS/NTFS
/dev/sda4         105,021,439   312,578,047   207,556,609   f W95 Ext d (LBA)
/dev/sda5         105,021,440   286,857,215   181,835,776   7 HPFS/NTFS
/dev/sda6         286,859,264   307,337,215    20,477,952   b W95 FAT32

/dev/sda1 overlaps with /dev/sda4

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="MEDIADIRECT" UUID="7E76-3E03" TYPE="vfat" 
/dev/sda2: UUID="56E268C0E268A5C9" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="102C6CC02C6CA308" LABEL="OS" TYPE="ntfs" 
/dev/sda5: UUID="581EA0AE1EA0871A" LABEL="Data" TYPE="ntfs" 
/dev/sda6: LABEL="NEW VOLUME" UUID="285A-6290" TYPE="vfat" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda5 on /media/Data type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=1024


================================ sda1/BOOT.INI: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=1024

```


Humble assumptions from my side:
sda1 should be my DELL MEDIA DIRECT Drive
sda2 Windows vista Recovery Drive (E: Drive in windows)
sda3 VISTA OS (C: Drive in windows)
sda5 Data (D: Drive in windows)
sda6 Empty fat32 drive (planning to put ubuntu in this)

---

### Post by meierfra. on 2009-04-28
It seems your media direct partitions really needs to be a logical partition.  There is a small problems turning /dev/sda1 into a logical partition:  /dev/sda1 starts immediately after /dev/sda6 (your fat32) partition. But two logical partition need to be separated by at least 63 sectors. 

To solve that problem, I suggest to shrink /dev/sda6 while you rewrite the partition table.  This will mess up the filesystem. But since there is nothing on that partition, you can just use gparted   to format it to ext3 or ext4.

If this sounds good to you,  download the attached file PT.txt and rewrite your partition table just as before.

I'm not a 100% sure that this will prevent media direct from writing the partition table again  So you should install Ubuntu before you use the Media Direct Button.

Are you actually using  Media Direct? If not,  you might consider deleting the Media Direct partition  and disable the Media Direct Button. (or you can use the media direct button to boot directly into Ubuntu and the power button to boot Vista)

---

### Post by karth83 on 2009-04-28
> **meierfra. said:**
> 

I'm not a 100% sure that this will prevent media direct from writing the partition table again  So you should install Ubuntu before you use the Media Direct Button.

Are you actually using  Media Direct? If not,  you might consider deleting the Media Direct partition  and disable the Media Direct Button. (or you can use the media direct button to boot directly into Ubuntu and the power button to boot Vista)

If I install ubuntu and then press the Media Direct Button and if still corrupts the partition table, will i be able to boot into live cd and rewrite this partition?

Actually I searched many sites how to disable the media direct. But the answers are like I have to format my Hard Drive and again install vista and all those stuff. Which I dont want. If I can directly delete the media direct partition and install ubuntu and use that button to boot ubuntu, then I can try it.

---

### Post by meierfra. on 2009-04-28
> If I install ubuntu and then press the Media Direct Button and if still corrupts the partition table, will i be able to boot into live cd and rewrite this partition?
Yes. And you might not even have to rewrite the partition table. Ubuntu itself does not have a problem with the corrupted partition table. Only gparted does.


> Actually I searched many sites how to disable the media direct. But the answers are like I have to format my Hard Drive and again install vista and all those stuff.

Do you know which version of Media Direct you have (1,2 or 3)?

With Media Direct 3 it seems to be fairly easy  to redirect the Media direct button:

[http://digiwanderlust.blogspot.com/2008/04/dual-boot-boot-linux-using-dell-media.html](http://digiwanderlust.blogspot.com/2008/04/dual-boot-boot-linux-using-dell-media.html)

(But I recommend to use "count=63"  when  you  backup up the MBR.  At least some versions of Media Direct seem to use more than just the first sector of the hard drive. Also  instead of "timeout 0" I would use "timeout 2", so what you are still able to access the Ubuntu recovery mode, if needed)

I don't have any first hand experience with Media Direct, so I'm not sure whether the button still works if you delete the Media Direct partition, but I think it will.

---

### Post by karth83 on 2009-04-29
> **meierfra. said:**
> It seems your media direct partitions really needs to be a logical partition.  There is a small problems turning /dev/sda1 into a logical partition:  /dev/sda1 starts immediately after /dev/sda6 (your fat32) partition. But two logical partition need to be separated by at least 63 sectors. 

To solve that problem, I suggest to shrink /dev/sda6 while you rewrite the partition table.  This will mess up the filesystem. But since there is nothing on that partition, you can just use gparted   to format it to ext3 or ext4.



Thank you very much. Now the gparted from the live cd is detecting all the partitions. I havent Installed Ubuntu 9.04 yet, because work is calling me :). I will try the Dell Media Direct also and post the results.


63 sectors means 63 * 512bytes = 32256bytes, I should shrink from my sda6 right?

Thank you very much once again.

---

### Post by meierfra. on 2009-04-29
> 63 sectors means 63 * 512bytes = 32256bytes, I should shrink from my sda6 right?

Rewriting the partition table already  shrunk   /dev/sda6. (if you look at the file PT.txt you will see  that I   reduced the size of /dev/sda6 by 63).  So you just need to reformat the partition to fix the file system.

---

### Post by karth83 on 2009-04-29
> **meierfra. said:**
> Rewriting the partition table already  shrunk   /dev/sda6. (if you look at the file PT.txt you will see  that I   reduced the size of /dev/sda6 by 63).  So you just need to reformat the partition to fix the file system.

Ok I got it. Just for academic interest, I would like to learn about the partition table, its errors and correcting it. This will also help to solve if my friends have any problem regarding partition :). Can you provide any web site link for it, so that I can read from it. 

And I visited your source forge page. Nice. Good Work.

---

### Post by karth83 on 2009-04-30
I am posting from my new Ubuntu 9.04 - Ext4!!!
Graphics is really awesome.
Thank You for solving my partition problem :)

---

