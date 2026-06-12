---
title: "[SOLVED] Doesn't boot, just dumps me at grub&amp;gt;"
date: 2008-10-21
forum: General Help
---

### Post by Hibbo on 2008-10-21
Hello there! I'm new to the forum and newish to Linux.

I've been running Ubuntu 8.04 quite happily for a few months now, on my HP nc6320 laptop.  It is installed on a WD 250gB USB HDD (grub is on the USB drive itself, I removed my internal drive when I installed it after it knacked my MBR the first time i tried it - it's a work laptop and the fun police don't like us messing!)

It has been working fine(ish), but last night it froze, and I had to do a cold restart (force power off by holding the button down).  When it boots I see a very brief "GRUB loading..." flash, then it dumps me at the grub> prompt.  I am now out of my depth!  The boot and kernel commands just return errors.

I'm not sure if it's related, but for some time now it has been giving a GRUB error 16, and I have to start with the xxx.16 kernel, which works fine.

Is my drive trashed?  I really hope not as I have a lot of (unbacked-up or course!) data on there I really don't want to lose...

Thanks for any help, I'll go and find the Live CD...

---

### Post by caljohnsmith on 2008-10-21
I think the first place I would start would be doing an "fsck" on your Ubuntu partition(s) to see if there are any file system issues that need fixing. From your Live CD, you can do:
```
sudo fsck -y /dev/sdaX
```
And replace sdaX with the Ubuntu partition(s). Let me know what that returns, and also please post:
```
sudo fdisk -lu
```
And we can work from there. :)

---

### Post by tuxxy on 2008-10-21
You may need to [restore GRUB]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by Hibbo on 2008-10-23
> **caljohnsmith said:**
> I think the first place I would start would be doing an "fsck" on your Ubuntu partition(s) to see if there are any file system issues that need fixing. From your Live CD, you can do:
```
sudo fsck -y /dev/sdaX
```
And replace sdaX with the Ubuntu partition(s). Let me know what that returns, and also please post:
```
sudo fdisk -lu
```
And we can work from there. :)

Hi mate, thanks for the reply.

I've booted from the LiveCD and fsck tells me it's clean.

fdisk -lu gives three partitions on my USB drive; sdb1/2/5, 1 being boot, starting at 63, ID 83, Linux system
Sdb2 is ID 5 Extended. sdb5 is ID 82, Linux swap / Solaris

I'll try booting it again now...

---

### Post by Hibbo on 2008-10-23
Still the same :(

I'll try restoring grub as per Tuxxy's advide...

---

### Post by Hibbo on 2008-10-23
Just restored grub as per the quide - still exactly the same, just get dumped at the grub> prompt :(

The live CD could at least read the drive, so all my stuff's still there at least (so far!)

---

### Post by Hibbo on 2008-10-23
I have just tried the grub restore procedure from the grub> prompt presented when I boot from the USB drive, it still hasn't fixed it.

What I did notice is that it finds stage1 and stage2 on (hd0,0), but for stage3 it gives Error 15: File not found

Is this relevant?

Could it be something wrong with the Kernel as opposed to grub?

---

### Post by Hibbo on 2008-10-23
the 'boot' command give Error 8: Kernel must be loaded before booting

How does one load the Kernel? (Typing 'kernel' gives Error 1)

---

### Post by caljohnsmith on 2008-10-23
Hibbo, if it's not too much trouble, it would help if I could see the full output of:
```
sudo fdisk -lu
```
Also from your Live CD, please post the output of:
```
sudo mount /dev/sda1 /mnt
ls -lR /mnt/boot
cat /mnt/boot/grub/menu.lst

```
And lastly please post the full output of:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> blocklist /boot/grub/menu.lst
grub> quit
```
Go ahead and reboot, and if you still get the Grub prompt, try:
```
grub> cat (hd0,0)/boot/grub/menu.lst
```
And let me know if it prints out your menu.lst. Let me know how it goes. :)

---

### Post by C.S.Cameron on 2008-10-23
If you have a bunch of stuff you don't want to loose you can clone the disk to a second flash drive using the dd command.

I've noticed that some recent upgrades re-write menu.lst to root (1,0) from (0,0), (or similar).

If hitting Esc at grub will give you a boot menu, you can (temporarily) edit it by typing "e", and then "b" to boot.

Another possibility is that you have filled up your flash drive.
If this is so you will need to remove some data or obsolete packages.

---

### Post by Hibbo on 2008-10-24
Buggering ********!

Grub has somehow found its way on to my internal HDD, so windows won't boot either!  I actually took the internal drive out when I installed Ubuntu, as it fecked the MBR the first time.  I knew I should have taken it out before playing with these grub commands...  How can I remove grub from the internal drive and get windows to boot again?

I'm now running from a Live CD, I'll do the things you've posted and post the outcomes

Cheers

---

### Post by Hibbo on 2008-10-24
PS.  It's not a flashdrive, it's a proper external HDD, it got loads of room left on it!

---

### Post by Hibbo on 2008-10-24
As requested:
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3ae63ae6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   144819359    72409648+   7  HPFS/NTFS
/dev/sda2       144819360   156295439     5738040    c  W95 FAT32 (LBA)

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   476279054   238139496   83  Linux
/dev/sdc2       476279055   488392064     6056505    5  Extended
/dev/sdc5       476279118   488392064     6056473+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

I used sdc1 instead of sda1, as this is my linux drive
```

ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt
ubuntu@ubuntu:~$ ls - lR /mnt/boot
ls: cannot access -: No such file or directory
ls: cannot access lR: No such file or directory
/mnt/boot:
abi-2.6.24-16-generic             initrd.img-2.6.24-19-generic.bak
abi-2.6.24-19-generic             initrd.img-2.6.24-21-generic
abi-2.6.24-21-generic             initrd.img-2.6.24-21-generic.bak
config-2.6.24-16-generic          memtest86+.bin
config-2.6.24-19-generic          System.map-2.6.24-16-generic
config-2.6.24-21-generic          System.map-2.6.24-19-generic
grub                              System.map-2.6.24-21-generic
initrd.img-2.6.24-16-generic      vmlinuz-2.6.24-16-generic
initrd.img-2.6.24-16-generic.bak  vmlinuz-2.6.24-19-generic
initrd.img-2.6.24-19-generic      vmlinuz-2.6.24-21-generic
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=7bde20a2-ba1a-4fa8-8646-e0bc1eaea8a3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=7bde20a2-ba1a-4fa8-8646-e0bc1eaea8a3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=7bde20a2-ba1a-4fa8-8646-e0bc1eaea8a3 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7bde20a2-ba1a-4fa8-8646-e0bc1eaea8a3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7bde20a2-ba1a-4fa8-8646-e0bc1eaea8a3 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7bde20a2-ba1a-4fa8-8646-e0bc1eaea8a3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7bde20a2-ba1a-4fa8-8646-e0bc1eaea8a3 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

For the grub bit, I have substituted hd1 for hd0, as this is what (I think) the USB HDD is?
```

grub> find /boot/grub/stage1
 (hd1,0)

grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> blocklist /boot/grub/menu.lst
(hd1,0)314410320+11

grub> 
```

Thanks again for your help, but I must stress I am quite concerned about not being able to get in to windows!  This is a work laptop and I must be able to run windows, the whole idea was that Linux was COMPLETELY on the external drive (including grub!) so that if the laptop had to go back to the IT guys there was NO trace of any meddling.  So please; how can I get my windows MBR back?  Then I can worry about getting linux running again.  Business must take priority over pleasure :(

---

### Post by caljohnsmith on 2008-10-24
OK, first to restore the Windows MBR to your internal drive, you can do the following:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda bs=440 count=1
```
That should make it so you can boot your Windows internal drive with no more problems. According to the commands you ran, Grub should be successfully installed to the MBR of your external drive now. But according to that blocklist command your ran, your menu.lst is located at about the 161 GB mark on your Ubuntu drive; some BIOSes have a limitation where they can't access anything on the HDD past 137 GB, so that may be your problem. While you are in the Live CD, also post:
```
sudo grub
grub> blocklist (hd1,0)/boot/grub/stage2 
```

Try rebooting the USB drive, and when you get the grub prompt do:
```
grub> cat (hd0,0)/boot/grub/menu.lst
```
Does that show your menu.lst or does that return an error?

---

### Post by Hibbo on 2008-10-25
Thanks John, I've did as you said for the Windows MBR, fingers crossed...

```
ubuntu@ubuntu:~$ sudo apt-get install syslinux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mtools
Suggested packages:
  floppyd
The following NEW packages will be installed:
  mtools syslinux
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 557kB of archives.
After this operation, 1253kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com hardy/main mtools 3.9.11-0ubuntu1 [204kB]
Get:2 http://archive.ubuntu.com hardy/main syslinux 2:3.53-1ubuntu2 [353kB]
Fetched 557kB in 2s (245kB/s)    
Selecting previously deselected package mtools.
(Reading database ... 98223 files and directories currently installed.)
Unpacking mtools (from .../mtools_3.9.11-0ubuntu1_i386.deb) ...
Selecting previously deselected package syslinux.
Unpacking syslinux (from .../syslinux_2%3a3.53-1ubuntu2_i386.deb) ...
Setting up mtools (3.9.11-0ubuntu1) ...

Setting up syslinux (2:3.53-1ubuntu2) ...
ubuntu@ubuntu:~$ sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda bs=440 count=10+1 records in
0+1 records out
410 bytes (410 B) copied, 0.0107484 s, 38.1 kB/s

```

I'm guessing hd1 is sdb, so I've used that for the lookup command

```
grub> blocklist (hd0,0)/boot/grub/stage2

Error 17: Cannot mount selected partition

grub> blocklist (hd1,0)/boot/grub/stage2
(hd1,0)166592512+96,166592616+116

grub>
``` 

I'll give her a reboot and see what happens, cheers mate!

---

### Post by Hibbo on 2008-10-25
Back in Windows! (or M$ Windoze as I believe you Linux types say ;) )

Thanks for that, I wish I knew about that earlier in the year...!  If you don't mind, could you tell me exactly what those commands actually did please? 

The USB drive still just goes to the grub> prompt, but it did take a lot longer at the stage 1.5 loading..... screen, long enough to get my hopes up!

I typed the cat command in wrong, I'll try it again now.....

---

### Post by caljohnsmith on 2008-10-25
OK, to explain a little, that "dd" command you ran installed the syslinux MBR (Master Boot Record) to your Windows drive (sda); to give a quick background, all a Windows MBR does is look at the HDD partition table for whichever partition is marked active, i.e. bootable (and there should only be one partition marked as active on any HDD), and then the Windows MBR tries to boot the boot sector of that partition. That means of course that the Windows partition should be marked as active so that the Windows MBR will boot it, which is not a problem since that's what happens by default when you install Windows. 

But there are actually many boot loaders that can do exactly what the Windows MBR does, i.e. simply boot the active partition on the HDD, and the syslinux MBR is one of them. So you didn't really install a Windows MBR per se, you installed a boot loader to the MBR that does exactly the same thing as the Windows MBR. :)
> **Hibbo said:**
> ```

grub> blocklist (hd1,0)/boot/grub/stage2
(hd1,0)[COLOR="Red"]166592512+96,166592616+116[/COLOR]

``` 

To explain, the above numbers give the block (sector) offset of where the file is located from the beginning of the partition, which in your case is sdb1. That means the Grub stage2 file occupies sectors 166592512 through 166592607 (96 sectors), and also from 166592616 through 166592616 (116 sectors). The furthest sector from the start of the partition it occupies is 166592616, so that is:
```
166592616 sectors * 512 bytes/sector = ~85.3 GB
```
Therefore, the stage2 file is also 85.3 GB from the start of the HDD since it is in the first partition. So that basically tells us what I suspected; Grub's stage2 is within the 137 GB limit, so it gets loaded just fine, but the menu.lst, being at 161 GB, is outside that limit and doesn't get loaded. That's why you get dumped into the grub prompt instead of seeing the Grub menu I think. :)

So bottom line, I would recommend that you make a ~200 MB /boot partition at the beginning of your Ubuntu drive so all your boot files (including Grub) will always be within reach of your BIOS. You can do that from the Live CD with gparted:
```
gksudo gparted
```
Let me know how it goes or if you run into problems. :)

---

### Post by Hibbo on 2008-10-25
Cheers John, that makes sense.

The cat command gives an Error 18: Selected cylinder exceeds maximum supported by BIOS, which ties in with what you're saying.  Also, that is the error I was getting when it was trying to autoboot the x.x.x-19 Kernel.

Do I literally just create a new partition and make it bootable, or do I need to jig things around a bit?

Thanks again for all your help buddy! :)

---

### Post by caljohnsmith on 2008-10-25
> **Hibbo said:**
> 
Do I literally just create a new partition and make it bootable, or do I need to jig things around a bit?

Thanks again for all your help buddy! :)
You're welcome, I try to help out when I can. :) About setting up your /boot partition, here are the basic steps:
[LIST=1]
[*]Make the ~200 MB /boot partition at the beginning of your drive with gparted
[*]Move your entire /boot directory over to the new partition
[*]Modify your /boot/grub/menu.lst so that it uses the new boot partition
[*]If the new partition is not called sdb1, you'll have to reinstall Grub to the MBR
[*]Lastly, add to your /etc/fstab an entry to auto-mount the /boot partition on start up
[/LIST]
I think that covers everything. If you want help with the specifics, then first get your /boot partition set up, and then post:
```
sudo fdisk -lu
```
And we can work from there. :)

---

### Post by Hibbo on 2008-10-25
Right, GParted's running now, I've shrank sdb1 by 212MB, and made a new ext3 partition at the start.  I'll set it bootable and cross my fingers again.  Is it really this simple?

Gparted seems to be taking ages so I'm off for a pint...

---

### Post by Hibbo on 2008-10-26
```
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1          433755   476279054   237922650   83  Linux
/dev/sdb2       476279055   488392064     6056505    5  Extended
/dev/sdb3   *          63      433754      216846   83  Linux
/dev/sdb5       476279118   488392064     6056473+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

I've made a new partition at the start of the disk, it's bootable, but I am still just getting dumped at the grub> prompt.

Do I have to manually put the grub files on to the new partition?

---

### Post by caljohnsmith on 2008-10-26
> **Hibbo said:**
> 
I've made a new partition at the start of the disk, it's bootable, but I am still just getting dumped at the grub> prompt.

Do I have to manually put the grub files on to the new partition?
Did you maybe miss what I mentioned in post #19? Yes, you have to move your boot files, including Grub, to the new partition. Also, since the boot partition is sda3 and not sda1, you'll need to reinstall Grub to the MBR so that you can tell Grub to look on sda3 for all its boot files. And of course you'll also need to do the rest of the steps in post #19 to get everything working OK.

Here's the specific steps that you can do from the Live CD:
```
sudo mkdir /mnt/sdb1 /mnt/sdb3
sudo mount /dev/sdb1 /mnt/sdb1
sudo mount /dev/sdb3 /mnt/sdb3
sudo cp -ax /mnt/sdb1/boot /mnt/sdb3/.
gksudo gedit /mnt/sdb3/boot/grub/menu.lst

```
When gedit pulls up your menu.lst, change all your Ubuntu entries to use (hd0,2) instead of (hd0,0):
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		[COLOR="Red"](hd0,2)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=77677cb5-6e56-4936-a373-80c15de06bca ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
And also change the line that has "#groot=(hd0,0)" to:
```
#groot=(hd0,2)
```
Save and close your menu.lst, and then do:
```
sudo grub
grub> root (hd1,2)
grub> setup (hd1)
grub> quit
```
Then reboot, and see if you can boot into Ubuntu. If you can, the last thing you'll need to do is modify your /etc/fstab to mount the new sda3 /boot partition. Let me know if you can get this far, and then we can go from here.

---

### Post by Hibbo on 2008-10-26
](*,) Yes I completely missed what you said in post 19 - probably because I'm an idiot.

Right, that's all done.  The only thing I found was that grub didn't recognise (hd0,2), I've used (hd1,2), I'm I right in assuming that sd**b** in linux = (hd**1**) in grub?

Thanks for your patience here mate, it is GREATLY appreciated.

Reboot time........

---

### Post by caljohnsmith on 2008-10-26
> **Hibbo said:**
> ](*,) Yes I completely missed what you said in post 19 - probably because I'm an idiot.

Right, that's all done.  The only thing I found was that grub didn't recognise (hd0,2), I've used (hd1,2), I'm I right in assuming that sd**b** in linux = (hd**1**) in grub?

Thanks for your patience here mate, it is GREATLY appreciated.

Reboot time........
No problem, in fact you caught my mistake in my previous post: you should use "root (hd1,2)" and then "setup (hd1)", so I'm glad you understood what I meant even though my brain was obviously 404 when I typed that. Let me know what happens on reboot. :)

---

### Post by Hibbo on 2008-10-26
Right, I'm back in to Ubuntu! :)

However, only when booting kernel -16 :confused:

When it tries -21 by default, I get an Error 16: Inconsistent filesystem structure.
If I then select -19 from the menu I get an Error 18: Selected cylinder exceeds maximum supported by BIOS - which is what I've had for a while before this episode, I've just been using -16.  I must start addressing problems when they occur...

So, I'm back to where I was, but still have some probs.

Incidentally, this problem started when kernel-21 arrived, is this just coincidence? 

Thanks again pal...

---

### Post by Hibbo on 2008-10-26
Forgot to add; the 212MB partition is automatically mounted when the desktop appears...

---

### Post by caljohnsmith on 2008-10-26
I should have thought of this earlier, but I just realized that all the UUIDs for your partitions will be different with the partition changes; so as long as you are in Ubuntu on your HDD, do:
```
sudo blkid -c /dev/null
```
That will list the UUIDs for all your partitions. Also, I made the mistake of having you copy the boot directory to the new sdb3 partition instead of copying the contents of the boot directory. To correct that:
```
sudo mv /boot /boot.backup
sudo mkdir /boot
sudo mount /dev/sdb3 /boot
sudo rm -fr /boot/*
sudo cp -a /boot.backup/* /boot/.
```
If you get any errors from any of the above commands, do NOT proceed to do the rest of them as that could be dangerous. If it goes OK though, next open the menu.lst with:
```

gksudo gedit /boot/grub/menu.lst
```
And change the "#kopt" line to use the UUID for your Ubuntu main install (sdb1) similar to:
```
# kopt=root=UUID=77677cb5-6e56-4936-a373-80c15de06bca ro
```
So replace whichever UUID you have with the UUID for sdb1. And make sure the "groot" line is like I gave in my previous post. Also, for all your Ubuntu entries, remove the "/boot" from their entries:
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		[COLOR="Red"]/boot[/COLOR]/vmlinuz-2.6.24-19-generic root=UUID=77677cb5-6e56-4936-a37
3-80c15de06bca ro quiet splash
initrd		[COLOR="Red"]/boot[/COLOR]/initrd.img-2.6.24-19-generic
quiet
```
So remove the red "/boot" above in all your Ubuntu entries so you have:
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=77677cb5-6e56-4936-a37
3-80c15de06bca ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
quiet
```
Next do:
```
sudo update-grub
```
Next back up and open your fstab with:
```
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
```
And make sure your "/" root partition mount uses the new UUID for sdb1. Also you'll need to correct the UUID for your swap partition, or sdb5 in the fstab file. Lastly, add a line to mount your new /boot partition:
```
# /dev/sdb3 (boot partition)
UUID=77677cb5-6e56-4936-a373-80c15de06bca /boot ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
```
And change the UUID above to your the UUID of sdb3. Next check these two files:
```
gksudo gedit /etc/initramfs-tools/conf.d/resume
gksudo gedit /etc/uswsusp.conf
```
If either file comes up blank, don't do anything with it, but if the file shows a UUID, then change it to the UUID of your swap partition sdb5. Next run:
```
sudo update-initramfs -u -k all
```
And finally, reboot, and let me know if you get any Grub errors. :)

---

### Post by Hibbo on 2008-10-26
Well I have followed you instructions to the letter, it's reboot time!

I have set all the root and groot to hd**1**,2 not hd**0**,2 - is this correct?

---

### Post by Hibbo on 2008-10-26
Rebooting - see you on the other side..........................[-o<

---

### Post by caljohnsmith on 2008-10-26
> **Hibbo said:**
> Well I have followed you instructions to the letter, it's reboot time!

I have set all the root and groot to hd**1**,2 not hd**0**,2 - is this correct?
Actually no, that's not correct (amazingly I didn't goof that this time :)); on start up, Grub sees the order of drives as the BIOS boot order, so since you are booting your sdb drive, that will be (hd0). So you should be using (hd0,2) in your menu.lst.

---

### Post by Hibbo on 2008-10-26
Just in time! All changed to 0,2...

Really rebooting now!

---

### Post by Hibbo on 2008-10-26
Error 15!:mad:

Back on the Live CD.

Will check over everything to see if I've stuffed anything up..........

---

### Post by meierfra. on 2008-10-26
grub is still looking for stage2   in (hd0,2)/boot/grub. But since you moved the boot folder, stage 2 is now in (hd0,2)/grub.

Reinstalling grub will fix that problem:

> sudo grub
grub> root (hd1,2)
grub> setup (hd1)
grub> quit


Did  you have to change the  UUID for the Ubuntu partition? Or was it still the same?

---

### Post by Hibbo on 2008-10-26
yahahh!  I thought it might be something like that.  I am back in, but in a dodgy way (I made a boot folder in the 212MB partition and copied all the files in there, that must be where grub is still looking.)

I will boot the Live CD again, delete the boot folder, restore grub and party on down...

---

### Post by Hibbo on 2008-10-26
It lives! :p:p:p

All is well!  I even figured the last grub problem out myself :)

Thanks ever so much John, it's a wonder of the internet how someone will sit down and spend so much time helping someone they've never met and who is thousands of miles away.  Thanks again mate.  If you're ever unfortunate enough to be in the UK or I'm fortunate enough to be in Cali then I certainly buy you a pint...:)

The 212MB partition isn't visible from the system now, I assume it's merely a part of the OS and not presented as storage media.

Thanks again mate! :biggrin:

---

### Post by caljohnsmith on 2008-10-26
That's great news Hibbo, and I'm glad meierfra caught that last detail that I missed. It's great your setup is working now, and I'm glad I could lend a hand. If you're in California sometime, let me know, and maybe I can take you up on your offer! :) Cheers and have fun Ubuntu-ing. :)

---

