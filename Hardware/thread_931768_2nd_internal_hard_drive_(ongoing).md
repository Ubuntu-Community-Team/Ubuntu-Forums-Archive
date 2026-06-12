---
title: "2nd internal hard drive (ongoing)"
date: 2008-09-27
forum: Hardware
---

### Post by taranispa on 2008-09-27
Hi, complete newcomer here. I'm running Ubuntu Studio 8.04 and I'm trying to finish installation of my 2nd hard drive. I followed a previous thread ([http://ubuntuforums.org/showthread.php?t=560015](http://ubuntuforums.org/showthread.php?t=560015)) when I was getting problems trying to access the drive (I tried to edit the permissions and found that I couldn't). I would have posted there but couldn't for some reason.

I've got a 160gb HD (came from my powermac) that I formatted in Gparted (ext3 primary partition - no boot flags added - and showing as only 149.5gb - a problem?). I edited fstab via the terminal as per the previous thread (using my UUID). I next entered the mkdir instruction which returned "File exists"

Lastly I entered the instruction:

sudo mount /media/sdb1

and got:

mount: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail or so

I really am stuck now and cant get the disk mounted let alone read and write on it ...

can anyone help me?

Cheers!

:guitar:

---

### Post by cariboo on 2008-09-27
WHat does dmesg | tail say when you try to mount your drivs? in a terminal type:

```
dmesg | tail
```

Jim

---

### Post by taranispa on 2008-09-29
Hi, thanks for the reply. Dmesg returned:

arwyn@arwynsmusicpc:~$ dmesg | tail
[   51.818812] Bluetooth: RFCOMM ver 1.8
[   54.619093] [drm] Initialized drm 1.1.0 20060810
[   54.671606] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   54.671616] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   54.671687] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  131.409639] NET: Registered protocol family 10
[  131.409898] lo: Disabled Privacy Extensions
[  145.983013] UDF-fs: No VRS found
[  146.105987] ISO 9660 Extensions: Microsoft Joliet Level 3
[  146.158515] ISO 9660 Extensions: RRIP_1991A
arwyn@arwynsmusicpc:~$ 



I also checked in system log and when I tried to mount the HD I got:

EXT3 -FS: unrecognised mount option "utf8" or missing value.

I'm going to try editing fstab to 

/dev/sdb1         /media/storage   ext3   defaults   0 0 

and see if that does it.

:)

---

### Post by taranispa on 2008-09-29
Hi, thanks for the reply. Dmesg returned:

arwyn@arwynsmusicpc:~$ dmesg | tail
[   51.818812] Bluetooth: RFCOMM ver 1.8
[   54.619093] [drm] Initialized drm 1.1.0 20060810
[   54.671606] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   54.671616] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   54.671687] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  131.409639] NET: Registered protocol family 10
[  131.409898] lo: Disabled Privacy Extensions
[  145.983013] UDF-fs: No VRS found
[  146.105987] ISO 9660 Extensions: Microsoft Joliet Level 3
[  146.158515] ISO 9660 Extensions: RRIP_1991A
arwyn@arwynsmusicpc:~$ 



I also checked in system log and when I tried to mount the HD I got:

EXT3 -FS: unrecognised mount option "utf8" or missing value.

I'm going to try editing fstab to 

/dev/sdb1         /media/storage   ext3   defaults   0 0 

and see if that does it.

:)

---

### Post by taranispa on 2008-09-30
Further to the last post I edited /etc/fstab as I proposed and then used the sudo mount comand which worked a treat, then used the chmod command to give myself read/write permissions and I now have my HD working! 

:guitar:

---

