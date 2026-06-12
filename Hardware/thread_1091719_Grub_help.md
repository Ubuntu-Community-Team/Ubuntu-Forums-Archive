---
title: "Grub help"
date: 2009-03-09
forum: Hardware
---

### Post by DeltaFee on 2009-03-09
Hi, I have ubuntu on my laptop and it can"t boot. It gives an error 11. Not sure what to do I have tons of data on this comp. Thx!

---

### Post by meierfra. on 2009-03-09
In order to get a clearer picture of your setup, I suggest to boot from your Ubuntu Live CD (the Ubuntu install CD), download the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by DeltaFee on 2009-03-09
Results:
> 
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/hda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/hdc

hda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

hda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

hda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of hda6 and 
                       looks at sector 155334513 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/hda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/hda1    *             63    52,098,794    52,098,732   7 HPFS/NTFS
/dev/hda2          52,098,795   156,296,384   104,197,590   5 Extended
/dev/hda5         155,718,108   156,296,384       578,277  82 Linux swap / Solaris
/dev/hda6          52,098,921   155,718,044   103,619,124  83 Linux


Drive: hdc ___________________ _____________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/hdc: 732 MB, 732643328 bytes
255 heads, 63 sectors/track, 22 cylinders, total 357736 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


blkid -c /dev/null: ____________________________________________________________

/dev/hda1: TYPE="ntfs" 
/dev/hda5: UUID="9bec91c2-724d-4392-ac18-f973a3cdbd6a" TYPE="swap" 
/dev/hda6: UUID="04c6e721-bdf4-437e-883f-b0a36485087d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/evms/hda1: TYPE="ntfs" 
/dev/evms/hda5: UUID="9bec91c2-724d-4392-ac18-f973a3cdbd6a" TYPE="swap" 
/dev/evms/hda6: UUID="04c6e721-bdf4-437e-883f-b0a36485087d" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

unionfs on / type unionfs (rw)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)


================================ hda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


================================ hda1/BOOT.INI: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== hda6/boot/grub/menu.lst: ===========================

default 0
timeout 5

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
# kopt=root=UUID=04c6e721-bdf4-437e-883f-b0a36485087d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=04c6e721-bdf4-437e-883f-b0a36485087d

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
# defoptions=splash vga=792 quiet

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.27-13-generic
root		04c6e721-bdf4-437e-883f-b0a36485087d
kernel		/boot/vmlinuz-2.6.27-13-generic root=UUID=04c6e721-bdf4-437e-883f-b0a36485087d ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.27-13-generic
boot

title		Debian GNU/Linux, kernel 2.6.27-13-generic (recovery mode)
root		04c6e721-bdf4-437e-883f-b0a36485087d
kernel		/boot/vmlinuz-2.6.27-13-generic root=UUID=04c6e721-bdf4-437e-883f-b0a36485087d ro single
initrd		/boot/initrd.img-2.6.27-13-generic
boot

title		Debian GNU/Linux, kernel 2.6.27-12-generic
root		04c6e721-bdf4-437e-883f-b0a36485087d
kernel		/boot/vmlinuz-2.6.27-12-generic root=UUID=04c6e721-bdf4-437e-883f-b0a36485087d ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.27-12-generic
boot

title		Debian GNU/Linux, kernel 2.6.27-12-generic (recovery mode)
root		04c6e721-bdf4-437e-883f-b0a36485087d
kernel		/boot/vmlinuz-2.6.27-12-generic root=UUID=04c6e721-bdf4-437e-883f-b0a36485087d ro single
initrd		/boot/initrd.img-2.6.27-12-generic
boot

title		Debian GNU/Linux, kernel 2.6.27-11-generic
root		04c6e721-bdf4-437e-883f-b0a36485087d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=04c6e721-bdf4-437e-883f-b0a36485087d ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.27-11-generic
boot

title		Debian GNU/Linux, kernel 2.6.27-11-generic (recovery mode)
root		04c6e721-bdf4-437e-883f-b0a36485087d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=04c6e721-bdf4-437e-883f-b0a36485087d ro single
initrd		/boot/initrd.img-2.6.27-11-generic
boot

title		Debian GNU/Linux, kernel 2.6.27-7-generic
root		04c6e721-bdf4-437e-883f-b0a36485087d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=04c6e721-bdf4-437e-883f-b0a36485087d ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.27-7-generic
boot

title		Debian GNU/Linux, kernel 2.6.27-7-generic (recovery mode)
root		04c6e721-bdf4-437e-883f-b0a36485087d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=04c6e721-bdf4-437e-883f-b0a36485087d ro single
initrd		/boot/initrd.img-2.6.27-7-generic
boot

title		Debian GNU/Linux, kernel 2.6.24-23-generic
root		04c6e721-bdf4-437e-883f-b0a36485087d
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=04c6e721-bdf4-437e-883f-b0a36485087d ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.24-23-generic
boot

title		Debian GNU/Linux, kernel 2.6.24-23-generic (recovery mode)
root		04c6e721-bdf4-437e-883f-b0a36485087d
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=04c6e721-bdf4-437e-883f-b0a36485087d ro single
initrd		/boot/initrd.img-2.6.24-23-generic
boot

title		Debian GNU/Linux, kernel memtest86+
root		04c6e721-bdf4-437e-883f-b0a36485087d
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


=============================== hda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=04c6e721-bdf4-437e-883f-b0a36485087d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9bec91c2-724d-4392-ac18-f973a3cdbd6a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sda1 /media/XP ntfs-3g defaults 0 0

=================== hda6: Location of files loaded by Grub: ===================


  79.4GB: boot/grub/menu.lst
  79.5GB: boot/grub/stage2
  79.5GB: boot/initrd.img-2.6.24-23-generic
  79.5GB: boot/initrd.img-2.6.24-23-generic.bak
  79.5GB: boot/initrd.img-2.6.27-11-generic
  79.4GB: boot/initrd.img-2.6.27-12-generic
  79.4GB: boot/initrd.img-2.6.27-13-generic
  79.5GB: boot/initrd.img-2.6.27-7-generic
  79.5GB: boot/vmlinuz-2.6.24-23-generic
  79.5GB: boot/vmlinuz-2.6.27-11-generic
  79.5GB: boot/vmlinuz-2.6.27-12-generic
  79.5GB: boot/vmlinuz-2.6.27-13-generic
  79.5GB: boot/vmlinuz-2.6.27-7-generic
  79.4GB: initrd.img
  79.4GB: initrd.img.old
  79.5GB: vmlinuz
  79.5GB: vmlinuz.old


---

### Post by meierfra. on 2009-03-09
Somehow your menu.lst got messed up. To fix it, boot from your live cd, open a terminal and type

```
sudo mount /dev/hda6 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```

This will open  the file "menu.lst".

Change all the lines

[COLOR="Red"]root[/COLOR] 04c6e721-bdf4-437e-883f-b0a36485087d


to

[COLOR="Red"]uuid[/COLOR] 04c6e721-bdf4-437e-883f-b0a36485087d


Also add this to the very bottom of the file:

title Windows XP
root (hd0,0)
chainloader +1

Save the file. Hopefully that will be all it takes  to fix your problem.

---

### Post by romer3r on 2009-03-12
meierfra, congratulations for your solution, I was reading a lot of forums tryin to fix my Error 11 problem with out success until now.

I replace the root by uuid on menu.lst and my intrepid works again,

my usplash is missing but i will work on that tomorrow.

Regards.

---

### Post by meierfra. on 2009-03-12
> my usplash is missing

Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1038055]("http://ubuntuforums.org/showthread.php?t=1038055")

---

