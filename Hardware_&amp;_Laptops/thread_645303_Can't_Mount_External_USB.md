---
title: "Can't Mount External USB"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by Snipir on 2007-12-19
Hello. I've been using Ubuntu for about a month and a half ago.


 Before, my entire hard drive was entirely dedicated to Ubuntu, but about a week ago, I decided to dedicate 1/3 of my disk to Windows so i could play games without so much hassle. 


Well, after searching a few forums, i came across GParted and used that to resize my partitions. Imoved my Ubuntu boot partition from Hard Drive (0,0) to Hard drive (0,1). Windows boots from Hard drive (0,0). I have no idea what Hard Drive (0,3) does - It was made by defualt when I installed Ubuntu. I had no idea what i was doing when i installed ubuntu, so i let it set up its default partitions and sizes (boot, /home, /user/ ect.).  


Anyways, after I set up windows, its boot loader over rode and replaced my GRUB boot loader, so i used      
    sudo grub

    > root (hd0,1)

    > setup (hd0)

    > quit.

That brought back my GRUB loader, but my loader kept attempting to boot from my old hard drive set up (It thought ubuntu was still (0,0)  ). So i went in and changed it to (0,1).   THen i added Windows and deleted my older kernels from my boot loader with   

sudo gedit /boot/grub/menu.lst



Now, whenever i plug in a USB device, my ubuntu tells me that i cannot mount it. I get the message, "Cannot Mount volume".  Today, i plugged a Memory Stick Pro Duo into a USB adapter it came with and got the "Cannot Mount Volume" error. The details said "Mount: wrong fs type, bad option, bad superblock on   /dev/sda, missing codepage or helper program, or other error     In some cases, useful info is found in syslog - try dmesg I tail or so."  

I typed  dmesg in my terminal and got

: 0 ANSI: 0
[  216.060167] SCSI device sda: 1947648 512-byte hdwr sectors (997 MB)
[  216.061042] sda: Write Protect is off
[  216.061047] sda: Mode Sense: 03 00 00 00
[  216.061053] sda: assuming drive cache: write through
[  216.063162] SCSI device sda: 1947648 512-byte hdwr sectors (997 MB)
[  216.180876] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[  216.573270] sda: Write Protect is off
[  216.573277] sda: Mode Sense: 03 00 00 00
[  216.573282] sda: assuming drive cache: write through
[  216.573291]  sda: sda1
[  216.574527] sd 2:0:0:0: Attached scsi removable disk sda
[  216.584171] sd 2:0:0:0: Attached scsi generic sg0 type 0
[  216.842524] FAT: Unrecognized mount option "usefree" or missing value
[  284.737254] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[  323.572164] usb 1-5: USB disconnect, address 3
[  418.745603] usb 1-5: new high speed USB device using ehci_hcd and address 4
[  418.891477] usb 1-5: configuration #1 chosen from 1 choice
[  418.891717] scsi3 : SCSI emulation for USB Mass Storage devices
[  418.891858] usb-storage: device found at 4
[  418.891862] usb-storage: waiting for device to settle before scanning
[  423.887717] usb-storage: device scan complete
[  423.888339] scsi 3:0:0:0: Direct-Access     SanDisk  SDDR-117         1.03 PQ: 0 ANSI: 0
[  424.146672] SCSI device sda: 1947648 512-byte hdwr sectors (997 MB)
[  424.147545] sda: Write Protect is off
[  424.147551] sda: Mode Sense: 03 00 00 00
[  424.147556] sda: assuming drive cache: write through
[  424.149666] SCSI device sda: 1947648 512-byte hdwr sectors (997 MB)
[  424.150542] sda: Write Protect is off
[  424.150547] sda: Mode Sense: 03 00 00 00
[  424.150551] sda: assuming drive cache: write through
[  424.150554]  sda: sda1
[  424.151501] sd 3:0:0:0: Attached scsi removable disk sda
[  424.151553] sd 3:0:0:0: Attached scsi generic sg0 type 0
[  424.342257] FAT: Unrecognized mount option "usefree" or missing value
[  518.427982] SCSI device sda: 1947648 512-byte hdwr sectors (997 MB)
[  518.428857] sda: Write Protect is off
[  518.428862] sda: Mode Sense: 03 00 00 00
[  518.428867] sda: assuming drive cache: write through
[  518.429729] SCSI device sda: 1947648 512-byte hdwr sectors (997 MB)
[  518.430603] sda: Write Protect is off
[  518.430606] sda: Mode Sense: 03 00 00 00
[  518.430608] sda: assuming drive cache: write through
[  518.430611]  sda: sda1
[  518.551388] FAT: Unrecognized mount option "usefree" or missing value
[  586.353135] SCSI device sda: 1947648 512-byte hdwr sectors (997 MB)
[  586.354009] sda: Write Protect is off
[  586.354013] sda: Mode Sense: 03 00 00 00
[  586.354016] sda: assuming drive cache: write through
[  586.355007] SCSI device sda: 1947648 512-byte hdwr sectors (997 MB)
[  586.355882] sda: Write Protect is off
[  586.355885] sda: Mode Sense: 03 00 00 00
[  586.355887] sda: assuming drive cache: write through
[  586.355891]  sda: sda1
[  586.479035] FAT: Unrecognized mount option "usefree" or missing value
[  596.207440] usb 1-5: reset high speed USB device using ehci_hcd and address 4



I know that my USB  ports arnet dead - my Windows partition can read USB devices. Did i just delete the wrong kernel and am booting from my old kernel? I know this is long and complicated, but can anyone help me? And if you can, please put it in simple terms without getting to technical please. =] Thanks you!

---

### Post by crouton on 2007-12-20
The second-to-last line is the problem - 'unrecognized mount option "usefree" or missing value'.

Read [this Launchpad bug submission]("https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025") for suggestions.

---

