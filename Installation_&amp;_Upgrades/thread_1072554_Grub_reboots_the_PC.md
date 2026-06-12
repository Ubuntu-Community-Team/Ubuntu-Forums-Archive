---
title: "Grub reboots the PC"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by runningdeere on 2009-02-17
Hi, 

I have a new installation of 8.10 which will not boot.
When the PC boots it goes through the usual BIOS screens, and then displays 'Grub loading Stage 1_5'
It then immediately reboots.

Ubuntu is installed on a 200G SATA drive, partitioned with 'Guided' partioning to use the whole disc.

If I boot from the Live CD GParted shows:
/dev/sd1     ext3      185Gb   boot
/dev/sda2    extended  4.3Gb
/dev/sda5    linux-swap  4.3Gb

I am new to Linux, but I read that as the first partition is bootable.

Can anybody help with this?

Thanks

---

### Post by caljohnsmith on 2009-02-17
It sounds like there might be an issue with how your HDD is set up in BIOS, but first it would help to make sure Grub is properly installed and is not the problem; how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by runningdeere on 2009-02-17
OK, well here it is in all it's gory detail:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2b832b82

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   389,190,689   389,190,627  83 Linux
/dev/sda2         389,190,690   398,283,479     9,092,790   5 Extended
/dev/sda5         389,190,753   398,283,479     9,092,727  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="34027aba-9697-455a-8a00-73f1a6031d7e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="c46b42f8-6888-423b-b8f5-ea64c3df1c90" TYPE="swap" 
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


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=34027aba-9697-455a-8a00-73f1a6031d7e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=34027aba-9697-455a-8a00-73f1a6031d7e

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		34027aba-9697-455a-8a00-73f1a6031d7e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=34027aba-9697-455a-8a00-73f1a6031d7e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		34027aba-9697-455a-8a00-73f1a6031d7e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=34027aba-9697-455a-8a00-73f1a6031d7e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		34027aba-9697-455a-8a00-73f1a6031d7e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=34027aba-9697-455a-8a00-73f1a6031d7e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c46b42f8-6888-423b-b8f5-ea64c3df1c90 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  24.6GB: boot/grub/menu.lst
  24.5GB: boot/grub/stage2
  24.6GB: boot/initrd.img-2.6.27-7-generic
  24.5GB: boot/vmlinuz-2.6.27-7-generic
  24.6GB: initrd.img
  24.5GB: vmlinuz
```


The drive is a SATA drive which is connected to an ABIT AT7-MAX2 M/B which uses a Highpoint SATA RAID controller. (approx 6 years old) - Windows needs drivers installing just to install, so we're a step in front there already.

Thankyou.

---

### Post by caljohnsmith on 2009-02-17
As I expected, the results of that script show that Grub and Ubuntu are installed OK, so I think you have a BIOS issue. How about going into your BIOS and let me know what HDD-related settings you have available for your HDD, such as "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, legacy IDE, native IDE, ACPI, DMA, etc. Also, check your BIOS boot order and make sure the HDD is the first drive to be booted. Please let me know what you come up with.

---

### Post by runningdeere on 2009-02-18
Unfortunately there's not a lot I can tell you, as options in the BIOS are pretty much non-existant.
There's the usual stuff for the IDE channels, but the drive is connected to a SATA controller which has it's own BIOS (Highpoint HPT374 built onto M/B - BIOS ver 1.23)
If I go in to the settings on this it tells me the drive is in ATA/133 mode, but I am unable to change anything apart from selecting the boot device. This drive is selected as the boot device (as it's the only one)
If I disable the HPT374 in the main BIOS then of course I get a disk boot failure.

Win XP was booting fine of this drive in its current configuration only a few days ago.

Is there anything else I could try?

Thankyou for your help.

---

### Post by caljohnsmith on 2009-02-18
OK, let's try an experiment to see what difference it makes in the booting behavior; from your Live CD, how about doing:
```
sudo grub
grub> root (hd0,0)
grub> install /boot/grub/stage1 (hd0) /boot/grub/stage2 p /boot/grub/menu.lst
grub> quit
```
Then let me know exactly what happens when you try to boot the HDD again.

---

### Post by runningdeere on 2009-02-18
OK Thanks, well we definitely have progress!

I now get a grub> command line.
(couldn't make my mind up if menu.lst was with a lower case L or a number 1)
- if I type a muber 1 I get the command prompt.
- When I tried it with a lower case L I got the Ubuntu loading screen but it never progressed from there.

---

### Post by caljohnsmith on 2009-02-18
> **runningdeere said:**
> OK Thanks, well we definitely have progress!

I now get a grub> command line.
(couldn't make my mind up if menu.lst was with a lower case L or a number 1)
- if I type a muber 1 I get the command prompt.
- When I tried it with a lower case L I got the Ubuntu loading screen but it never progressed from there.
So you got the Grub command prompt, but how did you load the menu.lst? Did you use the "configfile" command? Did you actually get the Grub menu, and then when you chose Ubuntu, Ubuntu wouldn't boot past the splash screen? Please give more details if you would like help.

---

### Post by runningdeere on 2009-02-19
Sorry for the delay in responding, I have been having some problems getting the Live CD to load again. I've taken out some memory and all now seems fine.

- If i used menu.1st, then it goes straight to a command prompt. (Something else does flash up first, but it's so quick I can't see it)

- If I use menu.lst, then I get a message saying press ESC to enter menu. I can get to the Grub menu, which shows me 3 options for Ubuntu, Recovery Mode and Memory Test.
Selecting the first one gives me the black Ubuntu loading screen with the orange bar moving side to side, but there is no disc activity, and it just sits there.

Trying Recovery mode gives me a stream of messages as drivers etc load up, but one message that stuck out was:
ata4.01 failed to IDENTIFY - I/O Error

The Memory Test option completes without errors

---

### Post by Sebjectivist on 2009-06-13
> **caljohnsmith said:**
> OK, let's try an experiment to see what difference it makes in the booting behavior; from your Live CD, how about doing:
```
sudo grub
grub> root (hd0,0)
grub> install /boot/grub/stage1 (hd0) /boot/grub/stage2 p /boot/grub/menu.lst
grub> quit
```
Then let me know exactly what happens when you try to boot the HDD again.

I was having the exact same problem with the same hardware. booting from sata on an Abit AT7-MAX2 mobo I bought especially to be able to boot from sata. It still confuses me that the boot menu in the bios doesn't show sata and you have to select IDE133RAID. 
Anyhow, first try with this experiment stopped the frustrating reboot problem, but jaunty didn't go all the way to the login screen. Then I disabled APIC in the bios and reinstalled with the noapic option from the F6 menu on the livecd, entered the grub commands again and finally I have an up and running system again :popcorn:

---

### Post by Sebjectivist on 2009-06-17
Hm, I enabled APIC in the bios again and it still works. performance is dabbling though.. but that [seems to be a problem]("http://ubuntuforums.org/showthread.php?t=1150108") with all older sata chips :(

---

