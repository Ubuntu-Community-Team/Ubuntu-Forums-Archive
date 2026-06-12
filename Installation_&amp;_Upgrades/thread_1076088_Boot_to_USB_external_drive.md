---
title: "Boot to USB external drive"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by vyco10 on 2009-02-21
I'd appreciate help on this. I installed Ubuntu 8.10 onto a hard drive that I had plugged into my laptop, but I am wanting to boot into this drive via USB. I'm pretty sure I have to edit the GRUB menu.lst file, but I don't know what to edit or what it edit it too.

Or am I wrong and I have to edit a number of other files as well? Thanks.

---

### Post by sgosnell on 2009-02-21
You should be able to boot to it by just making it the first boot device in your BIOS.  When the boot first starts, enter Setup via whatever hotkey your computer uses, and change the boot section to have it boot from the USB device.  You'll need to have it connected before starting the boot.

---

### Post by vyco10 on 2009-02-21
> **sgosnell said:**
> You should be able to boot to it by just making it the first boot device in your BIOS.  When the boot first starts, enter Setup via whatever hotkey your computer uses, and change the boot section to have it boot from the USB device.  You'll need to have it connected before starting the boot.

Well, I tried but I get a "No boot sector or USB device GRUB GRUB GRUB... ..." message.

---

### Post by caljohnsmith on 2009-02-21
> **vyco10 said:**
> Well, I tried but I get a "No boot sector or USB device GRUB GRUB GRUB... ..." message.
That sounds like it might be a problem with how your USB drive is configured in BIOS. But first, to see if Grub is correctly configured on your USB drive, how about downloading the **Boot Info Script** to your Ubuntu Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by vyco10 on 2009-02-21
> **caljohnsmith said:**
> That sounds like it might be a problem with how your USB drive is configured in BIOS. But first, to see if Grub is correctly configured on your USB drive, how about downloading the **Boot Info Script** to your Ubuntu Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

Well, my system is a Dell Latitude 110L, and the BIOS is up-to-date. I have no issues with booting up to Ubuntu on the USB flash drive I created with the Ubuntu Live CD. It may be an issue with the hdd portable casing that I put the drive in after installing, but it doesn't seem like it would be.

Here is the content of the RESULTS.txt file:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders, total 39070080 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe6fbe6fb

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     7,807,589     7,807,527   7 HPFS/NTFS
/dev/sda2           7,807,590    39,070,079    31,262,490   5 Extended
/dev/sda5           7,807,653    37,672,424    29,864,772  83 Linux
/dev/sda6          37,672,488    39,070,079     1,397,592  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="8EB0A3E2B0A3CF51" TYPE="ntfs" 
/dev/sda5: UUID="9a3f3ac2-016a-4783-bed7-e405198c589f" TYPE="ext3" 
/dev/sda6: UUID="617ac920-ee4e-4d4c-bfa0-a751dea6f615" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/windu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=windu)


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=9a3f3ac2-016a-4783-bed7-e405198c589f ro

## default grub root device
## e.g. groot=(sd0,0)
# groot=9a3f3ac2-016a-4783-bed7-e405198c589f

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
uuid		9a3f3ac2-016a-4783-bed7-e405198c589f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9a3f3ac2-016a-4783-bed7-e405198c589f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9a3f3ac2-016a-4783-bed7-e405198c589f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9a3f3ac2-016a-4783-bed7-e405198c589f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9a3f3ac2-016a-4783-bed7-e405198c589f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=9a3f3ac2-016a-4783-bed7-e405198c589f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=617ac920-ee4e-4d4c-bfa0-a751dea6f615 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  15.0GB: boot/grub/menu.lst
  15.0GB: boot/grub/stage2
  15.1GB: boot/initrd.img-2.6.27-7-generic
  15.0GB: boot/vmlinuz-2.6.27-7-generic
  15.1GB: initrd.img
  15.0GB: vmlinuz
```

I don't know, but I don't think I should be seeing ntfs on sd1. The only drive I have connected to my laptop right now is the internal hard drive that I installed Ubuntu on, the one that I want to configure to boot via USB once I pull it out of the laptop.

---

### Post by caljohnsmith on 2009-02-21
According to the script results, it looks like Grub is configured correctly to boot, and that's confirmed of course by the fact that you can boot that drive successfully when it is in your laptop. You shouldn't need to modify Grub's menu.lst or any other Grub files in order to boot that HDD when you put it in a USB enclosure, so I think the issue is probably with how you have your USB drive configured in your BIOS. How about going into your BIOS and let me know which HDD/USB related settings you have available, such as "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, legacy IDE, native IDE, ACPI, DMA, etc. We can work from there.

---

### Post by vyco10 on 2009-02-21
> **caljohnsmith said:**
> According to the script results, it looks like Grub is configured correctly to boot, and that's confirmed of course by the fact that you can boot that drive successfully when it is in your laptop. You shouldn't need to modify Grub's menu.lst or any other Grub files in order to boot that HDD when you put it in a USB enclosure, so I think the issue is probably with how you have your USB drive configured in your BIOS. How about going into your BIOS and let me know which HDD/USB related settings you have available, such as "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, legacy IDE, native IDE, ACPI, DMA, etc. We can work from there.

System
[INDENT]Boot Sequence - This list specifies the order that the BIOS searches devices when trying to find an OS. Only devices that are preceeded by a number are bootable.
[LIST=1]
[*]Diskette Drive
[*]Internal HDD
[*]USB Storage Device
[*]CD/DVD/CD-RW Drive
Cardbus NIC
Onboard NIC
[/LIST][/INDENT]

There is also a USB emulation option under POST Behavior options. That defines how the BIOS, in the absence of a USB-aware operating system, handles USB devices.

That's about the only information I have. Or rather, those are about the only options I have to choose from.

---

### Post by caljohnsmith on 2009-02-21
Have you tried changing the USB emulation option? Does that change the booting behavior at all?

---

### Post by PwnCakes193 on 2009-02-21
> **vyco10 said:**
> I'd appreciate help on this. I installed Ubuntu 8.10 onto a hard drive that I had plugged into my laptop, but I am wanting to boot into this drive via USB. I'm pretty sure I have to edit the GRUB menu.lst file, but I don't know what to edit or what it edit it too.

Or am I wrong and I have to edit a number of other files as well? Thanks.

I ran into this exact same thing last time. Reinstall ubuntu onto your hardrive, but this time take out your internal Hard drive so it installs GRUB straight onto the external HD

---

### Post by vyco10 on 2009-02-21
> **caljohnsmith said:**
> Have you tried changing the USB emulation option? Does that change the booting behavior at all?

I haven't tried that yet. I will and get back to you on that.

EDIT: That actually turned USB off. I didn't even have the option to boot into the "USB storage device" when I went into the boot menu.

> **PwnCakes193 said:**
> I ran into this exact same thing last time. Reinstall ubuntu onto your hardrive, but this time take out your internal Hard drive so it installs GRUB straight onto the external HD

Well, the "external" was internal when I installed it. See, my primary hard drive for the laptop is a 40 GB with Windows XP installed as the OS. I removed that drive and plugged this old 20 GB hard drive into the 40 GB's place and installed Ubuntu with it plugged in as an "internal" drive. But I took it out because I want to be able to boot that drive as an external USB hard drive and keep the 40GB as a Windows XP drive (for now, anyway).

Maybe my problem is that I should have installed Ubuntu onto the drive with it plugged into the USB casing as an external instead of plugged into the laptop as an internal.

EDIT - I'm going to try and reinstall Ubuntu onto the drive while it's plugged into the USB casing.

---

### Post by vyco10 on 2009-02-21
I tried re-installing Ubuntu onto the hard drive while plugged in via USB (with the internal hard drive pulled out) and it won't boot. But instead of it saying "No boot sector or USB device GRUB GRUB GRUB...." it just says "GRUB" and it goes no further than that.

I know something changed by installing it via USB, but it still won't boot.

EDIT: Just for added information, whether it helps or not, the hdd is an Hitachi Travelstar 20GB 4200RPM drive and the USB casing is an Apricorn encasing. This is a picture of it:

[IMG]http://www.hardwarezone.com/img/data/articles/2003/693/apricorn.jpg[/IMG]

---

