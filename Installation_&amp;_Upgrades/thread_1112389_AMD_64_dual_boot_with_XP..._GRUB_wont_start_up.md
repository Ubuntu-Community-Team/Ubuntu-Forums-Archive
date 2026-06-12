---
title: "AMD 64 dual boot with XP... GRUB wont start up"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by GodAmoungMen on 2009-03-31
I just loaded Ubuntu 8.10 on my notebook (AMD 64 turion MT28, xp pro was installed first) When I boot up the computer, GRUB does not start up, and the system just boots XP. I am a newbie and am not entirely sure about everything. I can only boot Ubuntu from the Live CD boot. How Can I get GRUB working?

---

### Post by Mark Phelps on 2009-04-01
When you installed Ubuntu, where did you install GRUB? If you used the liveCD and accepted the default, it installed to the MBR and you should be seeing a menu.  If you used the alternate CD, you may have installed GRUB to the Ubuntu partition.

---

### Post by GodAmoungMen on 2009-04-01
Yeah How can i figure out where
every time I do 

 sudo grub 

find /boot/grub/stage1 (I have also tried: find /grub/stage1)

I get an error 15 (I think that it cant find the file.)

I tried using wingrub, and it doesn't recognize ubuntu when I install. I followed pretty good directions on the install for XP home as well

---

### Post by meierfra. on 2009-04-01
In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by GodAmoungMen on 2009-04-01
Here it is. I am not terribly sure what it all means. I really want to give Ubunutu a chance but I still need windows xp for certain things so I need the Dual Boot.  I hope you can make some sense out of this. Thanks again for the help so far!


```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /GRLDR /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa845a845

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   114,736,229   114,736,167   7 HPFS/NTFS
/dev/sda2         149,308,110   156,296,384     6,988,275  49 Unknown
/dev/sda3         114,736,230   149,308,109    34,571,880   5 Extended
/dev/sda5         114,736,293   147,765,869    33,029,577  83 Linux
/dev/sda6         147,765,933   149,308,109     1,542,177  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="CAE4D03FE4D02F85" TYPE="ntfs" 
/dev/sda5: UUID="9bcd89bc-b43a-447a-9f88-553f5b280461" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="61f7d8ae-ed29-4820-bd0e-7c9bd0e17f01" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\GRLDR="Start Grub"

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=9bcd89bc-b43a-447a-9f88-553f5b280461 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=61f7d8ae-ed29-4820-bd0e-7c9bd0e17f01 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  64.5GB: boot/vmlinuz-2.6.27-7-generic
  64.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  b8 00 50 8e d0 bc ff ff  33 c0 8e d8 8e c0 bf 00  |..P.....3.......|
00000010  06 be 00 7c b9 00 02 f3  a4 6a 60 68 1f 00 cb b8  |...|.....j`h....|
00000020  40 00 8e c0 26 8b 1e 0e  00 83 fb 00 74 23 8e c3  |@...&.......t#..|
00000030  26 8b 0e 00 00 c1 e1 08  bf 00 00 66 b8 24 46 45  |&..........f.$FE|
00000040  4d f2 66 af 83 f9 00 74  08 83 ef 04 be 02 00 eb  |M.f....t........|
00000050  03 be 00 00 33 c0 8e c0  bb 00 08 b6 00 b2 80 b9  |....3...........|
00000060  0c 00 b8 01 02 cd 13 26  8b 47 06 c1 e8 09 81 c3  |.......&.G......|
00000070  00 02 b6 00 b2 80 b9 0d  00 b4 02 cd 13 8b c6 8b  |................|
00000080  df 0e 68 8b 00 68 80 00  6a 0a cb b9 0b 00 b2 80  |..h..h..j.......|
00000090  83 f8 00 74 0a 83 f8 02  74 05 b9 01 00 b2 00 33  |...t....t......3|
000000a0  c0 8e c0 bb 00 7c b6 00  b8 01 02 cd 13 80 fa 80  |.....|..........|
000000b0  75 0c be be 01 bf be 7d  b9 42 00 f3 2e a4 6a 00  |u......}.B....j.|
000000c0  68 00 7c 52 b9 10 00 6a  00 e2 fc 66 61 5a cb 00  |h.|R...j...faZ..|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  50 68 6f 65 6e 69 78 20  46 69 72 73 74 44 69 73  |Phoenix FirstDis|
00000110  6b 6a 10 b4 42 8b f4 cd  13 61 61 73 0e 4f 74 0b  |kj..B....aas.Ot.|
00000120  32 e4 8a 56 00 cd 13 eb  d6 61 f9 c3 49 6e 76 61  |2..V.....a..Inva|
00000130  6c 69 64 20 70 61 72 74  69 74 69 6f 6e 20 74 61  |lid partition ta|
00000140  62 6c 65 00 45 72 72 6f  72 20 6c 6f 61 64 69 6e  |ble.Error loadin|
00000150  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
00000160  65 6d 00 4d 69 73 73 69  6e 67 20 6f 70 65 72 61  |em.Missing opera|
00000170  74 69 6e 67 20 73 79 73  74 65 6d 00 00 00 00 00  |ting system.....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 2c 44 63  45 a8 45 a8 00 00 80 01  |.....,DcE.E.....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 27 bc d6 06 00 00  |......?...'.....|
000001d0  00 00 49 00 00 00 ce 42  e6 08 f3 a1 6a 00 00 fe  |..I....B....j...|
000001e0  ff ff 05 fe ff ff 66 bc  d6 06 68 86 0f 02 00 00  |......f...h.....|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda2

00000000  dd dd dd dd dd dd dd dd  dd dd dd dd dd dd dd dd  |................|
*
00000200



```

---

### Post by meierfra. on 2009-04-01
Did you have any error messages while installing Ubuntu? You are missing various important boot files and it looks like the installation did not quite finish. Try this:

Boot from the LiveCD, open a terminal   and do

```

sudo  mount /dev/sda5 /mnt 
sudo grub-install  --root-directory=/mnt --recheck /dev/sda
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt /bin/bash

```

and at the new prompt:

```

update-initramfs -c -k all 
update-grub
exit

```

Reboot and see whether you can boot into Ubuntu.
You still will have to edit menu.lst so that your are able to boot into Windows, but we'll  worry about that later.

The boot info script was not able to recognize  the 3.5 GB partition /dev/sda2. Do you know what's on where?

---

### Post by GodAmoungMen on 2009-04-02
AWESOME!!! Thanks for the help!! I can now load into Ubuntu. How do I setup up grub now so I can load windows? 

Oh, one thing. when I tried to shutdown Ubuntu, it seemed to stop, but still had the flashing cursor underscore. the text on the line above was 
```

[140.172974]type=1503 audit(12387078979.610:14) : operation="socket_creat" family="x25" sock_type="seqpacket" protocal=0 pid=6978 profile-"usr/sbin/cupsd"
```

---

### Post by GodAmoungMen on 2009-04-02
I have been having one more problem now. Every time I need to put in my password. I get an error window saying something like.
```

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.
```

I thought I was an administrator when I set the OS up?

---

### Post by meierfra. on 2009-04-02
Given all the problems you are having I suggest to check your LiveCD for errors (Boot from the LiveCD, the first screen will give you on option to check the CD for defects). If your CD is indeed defect, you might consider   to burn a new CD at a small speed and reinstall.

Are you using 32 bit or the 64 bit version of Ubuntu?


> [140.172974]type=1503 audit(12387078979.610:14) : operation="socket_creat" family="x25" sock_type="seqpacket" protocal=0 pid=6978 profile-"usr/sbin/cupsd"

Sorry, I have no idea  what could be causing this.


> the underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.


Post the output of

```
id
```

> How do I setup up grub now so I can load windows? 

Since "sudo" is not working, try this:

Boot into recovery mode:   Press "esc" during the  "3 2 1" countdown at boot up. The Grub  menu should appear. Then choose the second entry (recovery mode)

At the "root" prompt type

```
nano -B /boot/grub/menu.lst
```
This will open the file "menu.lst" in the commmand line editor "nano"

Change "timeout 3" to "timeout 10"
Change "hiddenmenu" to "#hiddenmenu"

Add

title Windows XP
root (hd0,0)
chainloader +1

to the very bottom of the file.

Save the file by pressing

```
Ctrl + O
Enter
Ctrl + X
```

Then reboot via

```
reboot
```
You should now automatically get the Grub Menu, where you can choose between Ubuntu and XP

---

### Post by GodAmoungMen on 2009-04-03
Got windows working again. Thanks. I did download the 64 bit version of Ubuntu. The CD didn't register anything when I checked for errors before I installed. I was considering just reinstalling the OS with a different disk a friend of mine got to work. When I initially tried to do this, I couldn't figure out how to do it without creating another partition (again I'm am not 100% sure of what I am doing).

here is the output of id.

```
andy@crested:~$ id
uid=1000(andy) gid=1000(andy) groups=4(adm),20(dialout),24(cdrom),46(plugdev),10
8(lpadmin),123(admin),124(sambashare),1000(andy)
```

---

### Post by meierfra. on 2009-04-03
> andy@crested:~$ id
uid=1000(andy) gid=1000(andy) groups=4(adm),20(dialout),24(cdrom),46(plugdev),10
8(lpadmin),123(admin),124(sambashare),1000(andy)

You are in the "admin" group.  So I have no idea what the problem could be.  I suggest to start a new thread. (include the error message, the output of "id" and also the output of "sudo cat /etc/sudoers")

> When I initially tried to do this, I couldn't figure out how to do it without creating another partition 


Do you have any problems other when the one already mentioned?  If not,   see whether you can fix the "sudo" problem before reinstalling.

But if you decide to reinstall, just choose "manual" partitioning, select your ubuntu partition, click on "edit partition"  and then select  "reformat"  and mount point "/". Otherwise just follow the directions on the screen.

---

