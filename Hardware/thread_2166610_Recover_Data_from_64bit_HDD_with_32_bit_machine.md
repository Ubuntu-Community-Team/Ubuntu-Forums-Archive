---
title: "Recover Data from 64bit HDD with 32 bit machine"
date: 2013-08-10
forum: Hardware
---

### Post by JamesKenny on 2013-08-10
Hello,

I have been using a Dell 1545 laptop for work (64 bit). Something in the board recently failed that charges the battery. I have already spent enough money trying to fix the problem via hardware including a new charger port (the little board inside of the laptop). The PC still works if I have a battery that is charged, I have tested it with a charged battery they guy who replaced my board had. My point is that I am certain that everything works except the battery charging port.

I also have a HP dc5100 desktop that is 32 bit. After trying to mount the drive from the laptop as a portable hard drive and trying to install the HDD as second internal drive for the last couple of days with no luck, today I remembered the laptop is 64 bit, the Desktop is 32 bit.

I do have most of my data stored elsewhere, but I also have some pretty important stuff left on the 64 bit drive. Is it possible to recover the data from the 64 bit drive with a 32 bit machine? BIOS does not recognise the drive exists.

Both machines run current ubuntu lts

---

### Post by steeldriver on 2013-08-10
If you are just trying to mount the drive and read the data, the host OS / CPU bus width should have no relevance - it would only be an issue if you are trying to actually boot the 64-bit system on the 32-bit platform

If the BIOS really does not see the laptop drive then you will need to figure that part out first

---

### Post by Bucky Ball on 2013-08-10
> **steeldriver said:**
> If you are just trying to mount the drive and read the data, the host OS / CPU bus width should have no relevance - it would only be an issue if you are trying to actually boot the 64-bit system on the 32-bit platform

If the BIOS really does not see the laptop drive then you will need to figure that part out first

Exactly. If you can't mount the drive, that is the problem. Nothing to do with '64 bit partition'. There isn't really such a thing. There is a 64bit OS installed on a partition, with the partition formatted in EXT, FAT, NTFS, HFS, whatever, and the 64bit OS is about how the OS interacts with the hardware on the machine. The data on the partition should be considered data on an EXT drive, or whatever the file system is. That's all. There is no such thing as a '64bit file'. For instance, an OpenOffice document file is neither 64bit or 32, it is just an OO file, regardless of what it is stored on.

As above, if the hard drive is not showing in the BIOS (or Gparted or anywhere) then you have a problem, but not to do with 64bit install. ;)

---

### Post by JamesKenny on 2013-08-10
> **steeldriver said:**
> 
If the BIOS really does not see the laptop drive then you will need to figure that part out first

I was scared you where going to say that. What I dont understand then is the laptop will boot and run normally with a charged battery and the hard drive installed. What else would cause it to not show up?

The drive is currently mounted internally, bios definately does not detect it

I am not seeing an I/O error with dmesg

lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 413c:3016 Dell Computer Corp. Optic 

james@james-HP-Compaq-dc5100-SFF:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=6bc99a46-318d-4e3c-aeea-77e1f3863a05 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=35559f41-4c68-424e-a1f2-c046e22c4868 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

---

### Post by Bucky Ball on 2013-08-10
No IO error as the drive is not mounted at BIOS time. Run this:
```

sudo blkid
```

See it? You say it is mounted internally. Do you mean you mounted it manually or it is an internal drive that is mounted? Please clarify. ;)

If you want it as an internal and mounting at boot, supply the info from the command I gave you so we can change the fstab to suit. Be aware that the processes the OS uses to mount internal and external drives are not identical. Because a drive will mount when used as an internal does not mean it will do the same when you put it in an external box/dock and plug it in.

---

### Post by JamesKenny on 2013-08-10
Sorry,

By mounted internally I meant, the hardware has power and the sata cable is plugged into sata port #2. Yes I have tested the both ports and power supplies with the boot hard drive (the one that is already in the desktop) with out any errors.

The hard drive I am having a problem with is a Toshiba MK2555GSX


james@james-HP-Compaq-dc5100-SFF:~$ sudo blkid
[sudo] password for james: 
/dev/sda1: UUID="6bc99a46-318d-4e3c-aeea-77e1f3863a05" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="391d550a-0d26-469e-b037-2195029aec6b" TYPE="swap"

---

### Post by Ranko Kohime on 2013-08-10
That dc5100 should have a 64-bit processor.  Disconnect the primary hard drive, connect the laptop drive to the primary port, and see if that works.

If it does, you probably have some setting in the BIOS to disallow multiple hard drives.

---

