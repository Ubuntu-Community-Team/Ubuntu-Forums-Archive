---
title: "How to undo unmounting your hard drive (recovering a Vista Partition)"
date: 2009-02-23
forum: Hardware
---

### Post by todoakaio on 2009-02-23
Summary:  Dual Boot Vista/Ubuntu -- Unmounted Hard drive -- See picture of problem below.

Ok, I admit it... I didn't understand entirely what "sudo unmount dev/sda1" would do (I was hoping it would unmount my USB drive), but when I booted up my computer the next morning, I got "No bootable device found.  Press F1 for retry, ...etc"  

So I popped in my handy dandy Ubuntu CD, and selected "Install" (Of course without the intention of actually installing it).  When it got to the partitions part, it showed a big fat nothing on my hard drive!  The only option was "Guided - Use entire disk"... Yeah right!  So I just quit, went to the desktop, and got on the internet for some troubleshooting help.

Then I got testdisk, which successfully made my computer recognize that there in fact was something there.  Then, I went into the grub terminal and put in (oh, what was it?) And it told me that my Linux partition, which had been till now on (hd0,4) was now on (hd0,5)!  Then after plugging in root(hd0,5) and setup(hd0), I was able to boot GRUB without the cd, and then get into my ubuntu partition.  

But it still won't let me get into Windows Vista.  The error message is something like Error 22:  No such partition.  So then I naturally went into the menu.lst, changed (hd0,3) to (hd0,4), and now the boot error goes something like Error 12: Invalid Device Requested.  Eh?  

And, here's a picture of my partitions with Gparted: 

My question is Why is it showing a picture of dev/sda1 all in one box?  Before, they were all different boxes, separate, but now, they're all in one big box with smaller boxes within.  

Hopefully someone can interpret this.  And, worse yet, I left my Windows Vista in Hibernate mode. (Therefore not being able to access them in Ubuntu... unless anyone knows a way to get to the files anyway?)   But I can still see the files when I use testdisk.  
Do I have to get the vista recovery CD?  Do I need to mess around with GRUB a bit more?  Do I have to somehow mount the whole drive again?  And what's with that grey box on the far left?  Someone please answer as many of these questions as you can!
Thanks

---

### Post by caljohnsmith on 2009-02-23
> **todoakaio said:**
> 
My question is Why is it showing a picture of dev/sda1 all in one box?  Before, they were all different boxes, separate, but now, they're all in one big box with smaller boxes within.  

The reason all your partitions appear to be within sda1 is because when you recovered your partitions with testdisk, you made them all logical partitions. sda1 is your extended partition, and an extended partition is just a container for your logical partitions. Vista should be on a primary partition normally, so it would have been better if you had recovered Vista as a primary partition in testdisk. Before going any further, how about posting the output of the following commands:
```
sudo fdisk -lu
sudo sfdisk -d
sudo mount /dev/sda5 /mnt && ls -l /mnt
```
And we can work from there if you want.

---

### Post by todoakaio on 2009-02-24
Yeah, sure.  I appreciate it!

```
sja@Todoakaio:~$ sudo fdisk -lu
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00054a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1        20547135   488392064   233922465    f  W95 Ext'd (LBA)
/dev/sda5        20561920   420083684   199760882+   7  HPFS/NTFS
/dev/sda6       420083748   485484299    32700276   83  Linux
/dev/sda7       485484363   488392064     1453851   82  Linux swap / Solaris

sja@Todoakaio:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start= 20547135, size=467844930, Id= f
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 20561920, size=399521765, Id= 7
/dev/sda6 : start=420083748, size= 65400552, Id=83
/dev/sda7 : start=485484363, size=  2907702, Id=82

sja@Todoakaio:~$ sudo mount /dev/sda5 /mnt && ls -l /mnt
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 /mnt -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 /mnt ntfs-3g force 0 0
sja@Todoakaio:~$ 

```

I can understand the last part.  I was in hibernate mode for Vista when I messed it up.

---

### Post by caljohnsmith on 2009-02-24
Since your Vista partition is not mountable, I think it would be good to run testdisk again to make sure you recovered the correct partition for Vista, or more specifically, make sure the start/stop sectors are exactly right. How about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select the sda HDD and "Proceed", "Intel", "Analyze", "Quick search", "Y" to search for Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also which of those partitions seem to be the partitions you want to recover (including your Vista partition of course). And lastly, please post the output of:
```
sudo fdisk -l
```
And we can work from there.

---

### Post by todoakaio on 2009-02-25
Ok, did all that you said.  Here's all the code you asked for, and more.

```
TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              5  25 21  1279 234 43   20480000 [RECOVERY]
P HPFS - NTFS           1279 234 44 26148 254 63  399521765 [My Computer]
P Linux                26149   1  1 30219 254 63   65400552
L Linux Swap           30220   1  1 30400 254 41    2907680




Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS found using backup sector!, 10485 MB / 10000 MiB

```The file system for the recovery drive:```

TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
   * HPFS - NTFS              5  25 21  1279 234 43   20480000 [RECOVERY]
Directory /

dr-xr-xr-x     0     0         0 25-Sep-2007 21:18 .
dr-xr-xr-x     0     0         0 25-Sep-2007 21:18 ..


```The file system for My Computer```

TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
   P HPFS - NTFS           1279 234 44 26148 254 63  399521765 [My Computer]
Directory /

dr-xr-xr-x     0     0         0 15-Jan-2009 21:14 .
dr-xr-xr-x     0     0         0 15-Jan-2009 21:14 ..
dr-xr-xr-x     0     0         0  2-Aug-2008 17:36 DELL
dr-xr-xr-x     0     0         0 30-Jun-2008 18:29 $RECYCLE.BIN
-r--r--r--     0     0        24  2-Aug-2008 17:29 autoexec.bat
dr-xr-xr-x     0     0         0  2-Aug-2008 17:29 Boot
-r--r--r--     0     0    333203  2-Aug-2008 17:29 bootmgr
dr-xr-xr-x     0     0         0  1-Dec-2008 08:41 CM60S
-r--r--r--     0     0        10 18-Sep-2006 15:43 config.sys
-r--r--r--     0     0      3167  2-Aug-2008 17:43 dell.sdr
dr-xr-xr-x     0     0         0  2-Aug-2008 17:38 doctemp
dr-xr-xr-x     0     0         0  2-Aug-2008 15:00 Documents and Settings
dr-xr-xr-x     0     0         0  2-Aug-2008 17:36 Drivers
dr-xr-xr-x     0     0         0 10-Jun-2008 16:17 EFI
-r--r--r--     0     0   3211198464  6-Jan-2009 19:52 hiberfil.sys
-r--r--r--     0     0         0  8-Sep-2008 14:34 IO.SYS
dr-xr-xr-x     0     0         0 27-Jan-2009 17:37 lc3
-r--r--r--     0     0         0  8-Sep-2008 14:34 MSDOS.SYS
dr-xr-xr-x     0     0         0  1-Sep-2008 12:11 MSOCache
-r--r--r--     0     0     26927  2-Aug-2008 15:00 newfile.enc
-r--r--r--     0     0     26927  2-Aug-2008 15:00 newkey
-r--r--r--     0     0   3525005312  6-Jan-2009 19:45 pagefile.sys
dr-xr-xr-x     0     0         0  2-Aug-2008 17:29 PerfLogs
dr-xr-xr-x     0     0         0  2-Aug-2008 17:29 Program Files
dr-xr-xr-x     0     0         0  2-Aug-2008 17:29 ProgramData
dr-xr-xr-x     0     0         0  2-Sep-2008 11:08 PSFONTS
dr-xr-xr-x     0     0         0 14-Jan-2009 16:25 System Volume Information
dr-xr-xr-x     0     0         0  2-Aug-2008 17:29 Users
dr-xr-xr-x     0     0         0  2-Aug-2008 17:29 Windows
dr-xr-xr-x     0     0         0 29-Oct-2008 22:52 Xilinx



Use Right arrow to change directory, c to copy,
    q to quit

```And Linux:```

TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
   P Linux                26149   1  1 30219 254 63   65400552
Directory /

drwxr-xr-x     0     0      4096  6-Feb-2009 22:30 .
drwxr-xr-x     0     0      4096  6-Feb-2009 22:30 ..
drwx------     0     0     16384 15-Jan-2009 23:02 lost+found
drwxr-xr-x     0     0      4096 29-Oct-2008 17:12 var
drwxr-xr-x     0     0     12288 25-Feb-2009 00:36 etc
drwxr-xr-x     0     0      4096 24-Feb-2009 23:18 media
lrwxrwxrwx     0     0        11 15-Jan-2009 23:02 cdrom
drwxr-xr-x     0     0      4096 16-Jan-2009 00:30 bin
drwxr-xr-x     0     0      4096 14-Feb-2009 23:41 boot
drwxr-xr-x     0     0      4096 29-Oct-2008 17:04 dev
drwxr-xr-x     0     0      4096 15-Jan-2009 23:11 home
drwxr-xr-x     0     0     12288 14-Feb-2009 23:41 lib
drwxr-xr-x     0     0      4096 20-Oct-2008 06:27 mnt
drwxr-xr-x     0     0      4096 21-Jan-2009 17:49 opt
drwxr-xr-x     0     0      4096 20-Oct-2008 06:27 proc
drwxr-xr-x     0     0      4096 23-Feb-2009 15:07 root
drwxr-xr-x     0     0      4096 22-Feb-2009 18:46 sbin
drwxr-xr-x     0     0      4096 29-Oct-2008 16:53 srv
drwxr-xr-x     0     0      4096 14-Oct-2008 07:02 sys
drwxrwxrwt     0     0      4096 25-Feb-2009 00:36 tmp
drwxr-xr-x     0     0      4096 29-Oct-2008 16:58 usr
lrwxrwxrwx     0     0        33  6-Feb-2009 22:30 initrd.img
lrwxrwxrwx     0     0        30  6-Feb-2009 22:30 vmlinuz
lrwxrwxrwx     0     0        29 16-Jan-2009 00:35 vmlinuz.9003
lrwxrwxrwx     0     0        32 16-Jan-2009 00:35 initrd.img.old
lrwxrwxrwx     0     0        29 16-Jan-2009 00:35 vmlinuz.old

Use Right arrow to change directory, c to copy,
    h to hide deleted files, q to quit


```The Last one, The Linux Swap, I couldn't get into.  But here's what showed up when I hit enter. (Below)  Is this what I want to be my partitions?```


TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63

     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              5  25 21  1279 234 43   20480000 [RECOVERY]
 2 P HPFS - NTFS           1279 234 44 26148 254 63  399521765 [My Computer]
 3 P Linux                26149   1  1 30219 254 63   65400552
 4 E extended LBA         30220   0  1 30401 254 63    2923830
 5 L Linux Swap           30220   1  1 30400 254 41    2907680










[  Quit  ]  [ Write  ]
                       Write partition structure to disk


```

And lastly, here's what sudo fdisk -l outputted:
```
sja@Todoakaio:~$ sudo fdisk -l
[sudo] password for sja: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00054a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1280       30401   233922465    f  W95 Ext'd (LBA)
/dev/sda5            1280       26149   199760882+   7  HPFS/NTFS
/dev/sda6           26150       30220    32700276   83  Linux
/dev/sda7           30221       30401     1453851   82  Linux swap / Solaris
sja@Todoakaio:~$ 



```
And just for more background information, I do have a recovery partition in there somewhere, I just never use it, and I would like it to continue what it usually does.

---

### Post by caljohnsmith on 2009-02-25
> **todoakaio said:**
> 
```
TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]P[/COLOR] HPFS - NTFS              5  25 21  1279 234 43   20480000 [RECOVERY]
[COLOR="Red"]*[/COLOR] HPFS - NTFS           1279 234 44 26148 254 63  399521765 [My Computer]
[COLOR="Red"]L[/COLOR] Linux                26149   1  1 30219 254 63   65400552
[COLOR="Red"]L[/COLOR] Linux Swap           30220   1  1 30400 254 41    2907680

```

OK, first you'll need to run the deep search again to get back to the above screen that shows the deep search results; once you've done that, I would recommend marking the partitions (using your right/left arrow keys) as shown above. It might be that testdisk won't let you mark the linux partition as "L", so if that happens, mark it as "P" instead. Once the partitions are marked exactly as shown above, then press enter to get the next screen, and choose "Write." Then reboot to your Live CD and please post the output of:
```
sudo fdisk -lu
sudo mount /dev/sda2 /mnt && ls -l /mnt
```
If you were able to make the Linux partition a logical partition ("L") in testdisk, then run the following commands to reinstall Grub to the MBR so that Grub uses the new partition:
```
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
```
Please post the output of the commands before typing "quit", and we can work from there.

---

### Post by todoakaio on 2009-02-27
Ok, all done.  Everything is working like you expect it to. I was able to get the Linux partition to be 'L', too.  Here's the output after rebooting after the live cd stuff. 
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00054a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           81920    20561919    10240000    7  HPFS/NTFS
/dev/sda2   *    20561920   420083684   199760882+   7  HPFS/NTFS
/dev/sda3       420083685   488392064    34154190    f  W95 Ext'd (LBA)
/dev/sda5       420083748   485484299    32700276   83  Linux
/dev/sda6       485484363   488392042     1453840   82  Linux swap / Solaris
```

```

ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt && ls -l /mnt
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 /mnt -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 /mnt ntfs-3g force 0 0


``````

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$ sudo grub

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

grub> 

```
What else do I need to do to get my Windows partition back up and running?

---

### Post by caljohnsmith on 2009-02-27
So can you boot into Ubuntu OK now? If so, how about doing that, and please post the output of the following commands:
```
cat /boot/grub/menu.lst
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda2
sudo mount -t ntfs-3g -o force /dev/sda2 /mnt && ls -l /mnt
```
And we can work from there.

---

### Post by todoakaio on 2009-02-27
Yes, I can boot back into ubuntu at this point.  
I did all of your codes one right after the other, so it'll be one big code.
```
sja@Todoakaio:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
splashimage=(hd0,4)/boot/grub/boote.xpm.gz
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=866ca084-a510-421b-a5c7-e70fe2bd1afb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=866ca084-a510-421b-a5c7-e70fe2bd1afb

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		866ca084-a510-421b-a5c7-e70fe2bd1afb
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=866ca084-a510-421b-a5c7-e70fe2bd1afb ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		866ca084-a510-421b-a5c7-e70fe2bd1afb
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=866ca084-a510-421b-a5c7-e70fe2bd1afb ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

#title		Ubuntu 8.10, kernel 2.6.27-9-generic
#uuid		866ca084-a510-421b-a5c7-e70fe2bd1afb
#kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=866ca084-a510-421b-a5c7-e70fe2bd1afb ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-9-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
#uuid		866ca084-a510-421b-a5c7-e70fe2bd1afb
#kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=866ca084-a510-421b-a5c7-e70fe2bd1afb ro  single
#initrd		/boot/initrd.img-2.6.27-9-generic

#title		Ubuntu 8.10, kernel 2.6.27-7-generic
#uuid		866ca084-a510-421b-a5c7-e70fe2bd1afb
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=866ca084-a510-421b-a5c7-e70fe2bd1afb ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-7-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#uuid		866ca084-a510-421b-a5c7-e70fe2bd1afb
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=866ca084-a510-421b-a5c7-e70fe2bd1afb ro  single
#initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		866ca084-a510-421b-a5c7-e70fe2bd1afb
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```You'll probably notice that I already changed the boot sector for the windows vista partition from (hd0,4) to (hd0,1).It seemed logical.  Bad part is when I rebooted, and selected Windows Vista/Longhorn it cleared the screen, said "Starting up..." and then restarted the whole computer, thus returning me to my dell splash screen, and then grub again.

And here's some more code.```

sja@Todoakaio:~$ sudo apt-get install ntfsprogs
[sudo] password for sja: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libntfs10
The following NEW packages will be installed:
  libntfs10 ntfsprogs
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 391kB of archives.
After this operation, 950kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libntfs10 ntfsprogs
Install these packages without verification [y/N]? y
Get:1 http://us.archive.ubuntu.com intrepid/main libntfs10 2.0.0-1ubuntu2 [122kB]
Get:2 http://us.archive.ubuntu.com intrepid/main ntfsprogs 2.0.0-1ubuntu2 [269kB]
Fetched 391kB in 0s (466kB/s)
Selecting previously deselected package libntfs10.
(Reading database ... 145157 files and directories currently installed.)
Unpacking libntfs10 (from .../libntfs10_2.0.0-1ubuntu2_i386.deb) ...
Selecting previously deselected package ntfsprogs.
Unpacking ntfsprogs (from .../ntfsprogs_2.0.0-1ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up libntfs10 (2.0.0-1ubuntu2) ...

Setting up ntfsprogs (2.0.0-1ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
sja@Todoakaio:~$ sudo ntfsfix /dev/sda2
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS volume version is 3.1.
NTFS partition /dev/sda2 was processed successfully.


```Hey!  didn't this part used to all be "logfile indicates unclean shutdown" and therefore unaccessable? ```

sja@Todoakaio:~$ sudo mount -t ntfs-3g -o force /dev/sda2 /mnt && ls -l /mnt
total 6578833
-rwxrwxrwx 1 root root         24 2006-09-18 15:43 autoexec.bat
drwxrwxrwx 1 root root       4096 2008-02-03 16:06 Boot
-rwxrwxrwx 1 root root     333203 2008-01-20 19:24 bootmgr
drwxrwxrwx 1 root root       4096 2009-01-27 18:09 CM60S
-rwxrwxrwx 2 root root         10 2006-09-18 15:43 config.sys
drwxrwxrwx 1 root root       8192 2008-09-01 11:59 DELL
-rwxrwxrwx 1 root root       3167 2008-08-02 17:43 dell.sdr
drwxrwxrwx 1 root root          0 2008-08-02 17:38 doctemp
drwxrwxrwx 1 root root          0 2008-08-02 15:00 Documents and Settings
drwxrwxrwx 1 root root          0 2008-09-02 09:02 Drivers
drwxrwxrwx 1 root root          0 2008-06-10 16:17 EFI
-rwxrwxrwx 1 root root 3211198464 2009-02-19 18:10 hiberfil.sys
-rwxrwxrwx 1 root root          0 2008-09-08 14:34 IO.SYS
drwxrwxrwx 1 root root       4096 2009-01-27 17:37 lc3
-rwxrwxrwx 1 root root          0 2008-09-08 14:34 MSDOS.SYS
drwxrwxrwx 1 root root          0 2008-09-01 12:11 MSOCache
-rwxrwxrwx 1 root root      26927 2008-08-02 15:00 newfile.enc
-rwxrwxrwx 1 root root      26927 2008-08-02 15:00 newkey
-rwxrwxrwx 1 root root 3525005312 2009-02-19 18:10 pagefile.sys
drwxrwxrwx 1 root root          0 2008-01-20 19:32 PerfLogs
drwxrwxrwx 1 root root       8192 2009-02-13 19:47 ProgramData
drwxrwxrwx 1 root root      28672 2009-02-12 19:10 Program Files
drwxrwxrwx 1 root root       4096 2008-10-03 17:43 PSFONTS
drwxrwxrwx 1 root root       4096 2008-09-01 12:04 $RECYCLE.BIN
drwxrwxrwx 1 root root      24576 2009-02-16 03:00 System Volume Information
drwxrwxrwx 1 root root       4096 2008-09-01 12:04 Users
drwxrwxrwx 1 root root      28672 2009-02-19 23:10 Windows
drwxrwxrwx 1 root root          0 2008-11-19 13:30 Xilinx
sja@Todoakaio:~$ 

```
Sweet, that looks like we're makin progress.  For some reason now, however, I can't find "My Computer" (From Vista) in my Places menu in Ubuntu anymore.  
I'm going to reboot my computer after this post, and then see if the Vista section boots up again.  If not, I'll boot back into Ubuntu, and see if I can mount into the vista partition.  Just one second.

---

### Post by todoakaio on 2009-02-27
Alright, so I rebooted, and the Windows Vista/Longhorn (loader) still isn't coming up.  When I select it from grub, it will clear the screen, display "Starting Up..." and then blank, and then restart to the dell splash, and then back to grub.  However, I *can* get into the My Computer from Ubuntu, now.  That's great progress, because now I can access all of the files like I used to!  So I guess the last step is to figure out how to boot into windows vista, if it's possible.

---

### Post by caljohnsmith on 2009-02-27
Do you have your Vista Install CD? If so, how about booting that, go to the command line, and run:
```
diskpart
```
And at the diskpart prompt do:
```
list volume
exit
```
Find the drive letter for your Vista partition, and then do:
```
chkdsk /r X:
```
But replace "X" with the drive letter of the Vista partition, and run the command as many times as it takes until it reports no errors. Then try booting Vista again and let me know how far you get.

---

### Post by todoakaio on 2009-03-04
So I got hold of a Vista repair cd and I booted from that, and I clicked on the option to repair, and before I could choose any options, it said, "Windows has found problems with your disk.  Would you like to automatically repair it?"  And I clicked yes.  It then rebooted right off the bat, and went to GRUB.  Then I selected Windows Vista/Longhorn (Loader) and it started the chkdsk automatically.  When it finished, it rebooted.  When I selected Windows Vista/Longhorn (Loader) again, it started loading, and my original vista screen (with my name and picture) finally came up!  So it worked.  Thank you so much man!  I appreciate it! 

This problem is solved.

---

