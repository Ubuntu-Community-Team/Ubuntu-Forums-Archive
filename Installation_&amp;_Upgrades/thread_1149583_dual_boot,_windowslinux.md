---
title: "dual boot, windows/linux"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by linux newb on 2009-05-05
hi im tying to dual boot on raid0 with windows and kubuntu 8.10, and i cant seem to get grub to ovewrite the windows bootloader, so im lookin at the boot list inside windows, can i just add the kubuntu installation to this list? i have installed kubuntu before windows this time hoping this way might work. i have already tried to install windows before kubuntu then add windows to grub. this way has worked in the past but now the guide is all screwed [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
and it doesnt work for me,can someone help me out plz?

---

### Post by caljohnsmith on 2009-05-05
RAID setups can be really tricky, but a good place to start concerning your boot problems would be to download the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by linux newb on 2009-05-05
> **caljohnsmith said:**
> RAID setups can be really tricky, but a good place to start concerning your boot problems would be to download the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

so what i need to do is boot into the kubuntu partition, or can i use a live cd, also, by installing windows first then kubuntu?

---

### Post by caljohnsmith on 2009-05-05
> **linux newb said:**
> so what i need to do is boot into the kubuntu partition, or can i use a live cd, also, by installing windows first then kubuntu?
You can run that script from any Live CD. :)

John

---

### Post by linux newb on 2009-05-05
> **caljohnsmith said:**
> You can run that script from any Live CD. :)

John

awesome thx john will post what comes up

---

### Post by linux newb on 2009-05-05
here are my results:
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader? is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfaf3faf3

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   153,597,464   153,597,402  83 Linux
/dev/sda2         153,597,465   163,364,984     9,767,520   5 Extended
Invalid MBR Signature found
Empty Partition
/dev/sda3    *    163,364,985   316,962,449   153,597,465   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2004 MB, 2004877312 bytes
16 heads, 32 sectors/track, 7648 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  32     3,915,775     3,915,744   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="62dceca2-c48e-4548-8390-2487831269e5" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
/dev/sdc1: SEC_TYPE="msdos" UUID="3C58-DFD2" TYPE="vfat" 

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
```

---

### Post by linux newb on 2009-05-05
the vfat is a removable

---

### Post by linux newb on 2009-05-05
i just noticed, when i complete the installation of kubuntu after windows; i am typing in setup (hd4), and it tells me stage 1 and stage 2 are ok, but it tries to run stage 1_5 and they both fail, 16 sectors dont get imbedded and it says it failed but is not fatal. now the twist, i install kubuntu first and everytthing is well, 16 sectors get imbedded and it succeeds, i thought this piece of knowledge might be usefull.

---

### Post by caljohnsmith on 2009-05-05
So you didn't say specifically, but are you able to boot Kubuntu now? Or what is the status of your booting problem?

---

### Post by linux newb on 2009-05-05
my current status, both kubuntu and windows are installed on the raid array, only windows will boot, this go around i have installed windows first, kubuntu second, and i get the problem where i enter "setup (hd4)" and it doesnt embed the sectors, and fails to succeed that proccess. therefore i am left with windows boot loader. sorry for the confusion john

---

### Post by caljohnsmith on 2009-05-05
> **linux newb said:**
> my current status, both kubuntu and windows are installed on the raid array, only windows will boot, this go around i have installed windows first, kubuntu second, and i get the problem where i enter "setup (hd4)" and it doesnt embed the sectors, and fails to succeed that proccess. therefore i am left with windows boot loader. sorry for the confusion john
I guess I'm not understanding, because if you are trying to follow the Fake Raid tutorial that you linked to:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

In that tutorial you set your RAID drive as (hd0) using Grub's device command, like the example they give in the tutorial:
```
device (hd0) /dev/mapper/isw_beeaakeeaa_five 
```
So the setup command should be "setup (hd0)" and not "setup (hd4)". It would help if you could post the output from your terminal (or konsole) of all the steps of that tutorial if you would like help troubleshooting your Kubuntu RAID install.

---

### Post by linux newb on 2009-05-06
ok so i manipulated it enough so now i got kubuntu has been installed first, windows second, grub is installed successfully, i can boot from linux, but i try to select windows, and it says is Error 13: unrecognized or unsupported executable format. so i just need to somehow get grub to recognize the windows installation, can anyone help me with this?

---

### Post by linux newb on 2009-05-06
> **caljohnsmith said:**
> I guess I'm not understanding, because if you are trying to follow the Fake Raid tutorial that you linked to:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

In that tutorial you set your RAID drive as (hd0) using Grub's device command, like the example they give in the tutorial:
```
device (hd0) /dev/mapper/isw_beeaakeeaa_five 
```
So the setup command should be "setup (hd0)" and not "setup (hd4)". It would help if you could post the output from your terminal (or konsole) of all the steps of that tutorial if you would like help troubleshooting your Kubuntu RAID install.
ah yes i can definately post the outcome of each command

---

### Post by linux newb on 2009-05-06
```
ubuntu@ubuntu:~$ sudo apt-get install dmraid
Reading package lists... Done               
Building dependency tree                    
Reading state information... Done           
The following extra packages will be installed:
  libdmraid1.0.0.rc14                          
The following NEW packages will be installed:  
  dmraid libdmraid1.0.0.rc14                   
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 105kB of archives.
After this operation, 381kB of additional disk space will be used.
Do you want to continue [Y/n]?
Get:1 http://archive.ubuntu.com intrepid/main libdmraid1.0.0.rc14 1.0.0.rc14-2ubuntu12 [77.5kB]
Get:2 http://archive.ubuntu.com intrepid/main dmraid 1.0.0.rc14-2ubuntu12 [27.9kB]
Fetched 105kB in 1s (60.1kB/s)
Selecting previously deselected package libdmraid1.0.0.rc14.
(Reading database ... 94839 files and directories currently installed.)
Unpacking libdmraid1.0.0.rc14 (from .../libdmraid1.0.0.rc14_1.0.0.rc14-2ubuntu12_i386.deb) ...
Selecting previously deselected package dmraid.
Unpacking dmraid (from .../dmraid_1.0.0.rc14-2ubuntu12_i386.deb) ...
Processing triggers for man-db ...
Setting up libdmraid1.0.0.rc14 (1.0.0.rc14-2ubuntu12) ...

Setting up dmraid (1.0.0.rc14-2ubuntu12) ...
update-initramfs is disabled since running on a live CD

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
ubuntu@ubuntu:~$ sudo modprobe dm-raid4-5
ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "nvidia_djgahabd" already active
RAID set "nvidia_djgahabd1" already active
RAID set "nvidia_djgahabd3" already active
RAID set "nvidia_djgahabd4" already active
RAID set "nvidia_djgahabd5" already active
ubuntu@ubuntu:~$ cd /dev/mapper
ubuntu@ubuntu:/dev/mapper$ ls
control          nvidia_djgahabd1  nvidia_djgahabd4
nvidia_djgahabd  nvidia_djgahabd3  nvidia_djgahabd5
ubuntu@ubuntu:/dev/mapper$

```
so this part is normal, be back to post rest, now i install.

---

### Post by caljohnsmith on 2009-05-06
As long as you have Kubuntu booting OK, there's no need any more to post all the steps you followed in that Fake Raid tutorial. How about instead posting your /boot/grub/menu.lst if you are still having problems booting Windows from Grub. We can work from there if you want.

John

---

### Post by linux newb on 2009-05-07
> **caljohnsmith said:**
> As long as you have Kubuntu booting OK, there's no need any more to post all the steps you followed in that Fake Raid tutorial. How about instead posting your /boot/grub/menu.lst if you are still having problems booting Windows from Grub. We can work from there if you want.

John
ok sure sorry about taking so long working late hours
here is the information i was talking about earlier anyway
```
grub> device (hd0) /dev/mapper/nvidia_djgahabd
device (hd0) /dev/mapper/nvidia_djgahabd      
grub> find /boot/grub/stage1
find /boot/grub/stage1      
 (hd0,4)                    
grub> root (hd0,4)          
root (hd0,4)                
grub> setup (hd4)
setup (hd4)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd4)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,4)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 d (hd4) /boot/grub/stage2 p /boot/grub/menu.lst "... failed

Error 21: Selected disk does not exist
```

---

### Post by linux newb on 2009-05-07
so at this point in time, i will have to go back and reinstall linux first, wondows second, and return to a live cd remount linux, and boot it up then get back to you seeing as to be able to get this error i must install windows first then linux, then do all this ..

---

### Post by linux newb on 2009-05-09
ok john, sorry for taking long again, here is my menu.lst file
```
menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts f$
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the de$
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the d$
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interact$
# control (menu entry editor and command-line)  and entries protect$
# command 'lock'
# e.g. password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options $

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/mapper/nvidia_djgahabd1 ro

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

## additional options to use with the default boot option, but not $
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


title           Ubuntu 8.10, kernel 2.6.27-7-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-7-generic root=/dev/mapper/nvidia_djgahabd1 ro quiet splash
initrd          /boot/initrd.img-2.6.27-7-generic

title           Windows
root            (hd0,0)
makeactive
chainloader     +1

title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-7-generic root=/dev/mapper/nvidia_djgahabd1 ro  single
initrd          /boot/initrd.img-2.6.27-7-generic

title           Ubuntu 8.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by linux newb on 2009-05-14
k i really need help here can anyone else assist me with this?

---

