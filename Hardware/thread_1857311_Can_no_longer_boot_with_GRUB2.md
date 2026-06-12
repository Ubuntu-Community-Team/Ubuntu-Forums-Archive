---
title: "Can no longer boot with GRUB2"
date: 2011-10-10
forum: Hardware
---

### Post by Daniel350 on 2011-10-10
Apologies if this is in the wrong section.

I recently installed another F60 Corsair SSD into my system. Upon boot, I got the error (note, written from memory):

```
    error: device not found (006ad : ... etc)
```

Upon booting from the "Boot your O/S" on an (Arch Linux) Install CD (ie, used the CD's boot loader), I tried:

```
    sudo install-grub
    sudo update-grub

```
To no avail.
I checked my disks and found none with a GUID corresponding to that it claims it can't find (ironically, because it doesn't exist?).

So how can I rescue my system? I'm at least at the moment able to boot my O/S from my  Install CD and thus not unproductive, but I have no clue what to do next.
The sudo fdisk -l is thus:
```

    sudo fdisk -l
    
    Disk /dev/sda: 60.0 GB, 60022480896 bytes
    255 heads, 63 sectors/track, 7297 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x0003f85b
    
       Device Boot      Start         End      Blocks   Id  System
    /dev/sda1   *           1        6776    54421504   83  Linux
    /dev/sda2            6776        7298     4191233    5  Extended
    /dev/sda5            6776        7298     4191232   82  Linux swap / Solaris
    
    Disk /dev/sdb: 60.0 GB, 60022480896 bytes
    255 heads, 63 sectors/track, 7297 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x00000000
    
    Disk /dev/sdb doesn't contain a valid partition table
    
    Disk /dev/sdc: 250.1 GB, 250059350016 bytes
    255 heads, 63 sectors/track, 30401 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x1db61db5
    
       Device Boot      Start         End      Blocks   Id  System
    /dev/sdc1   *           1       30401   244196001    7  HPFS/NTFS

```

Disclaimer: my O/S is Ubuntu server 11.04 64bit

(For those with a Stack Exchange account: [http://askubuntu.com/questions/65047/can-no-longer-boot-with-grub2](http://askubuntu.com/questions/65047/can-no-longer-boot-with-grub2))

---

### Post by vidtek on 2011-10-10
> **Daniel350 said:**
> Apologies if this is in the wrong section.

I recently installed another F60 Corsair SSD into my system. Upon boot, I got the error (note, written from memory):

```
    error: device not found (006ad : ... etc)
```Upon booting from the "Boot your O/S" on an (Arch Linux) Install CD (ie, used the CD's boot loader), I tried:

```
    sudo install-grub
    sudo update-grub

```To no avail.
I checked my disks and found none with a GUID corresponding to that it claims it can't find (ironically, because it doesn't exist?).

So how can I rescue my system? I'm at least at the moment able to boot my O/S from my  Install CD and thus not unproductive, but I have no clue what to do next.
The sudo fdisk -l is thus:
```

    sudo fdisk -l
    
    Disk /dev/sda: 60.0 GB, 60022480896 bytes
    255 heads, 63 sectors/track, 7297 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x0003f85b
    
       Device Boot      Start         End      Blocks   Id  System
    /dev/sda1   *           1        6776    54421504   83  Linux
    /dev/sda2            6776        7298     4191233    5  Extended
    /dev/sda5            6776        7298     4191232   82  Linux swap / Solaris
    
    Disk /dev/sdb: 60.0 GB, 60022480896 bytes
    255 heads, 63 sectors/track, 7297 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x00000000
    
    Disk /dev/sdb doesn't contain a valid partition table
    
    Disk /dev/sdc: 250.1 GB, 250059350016 bytes
    255 heads, 63 sectors/track, 30401 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x1db61db5
    
       Device Boot      Start         End      Blocks   Id  System
    /dev/sdc1   *           1       30401   244196001    7  HPFS/NTFS

```Disclaimer: my O/S is Ubuntu server 11.04 64bit

(For those with a Stack Exchange account: [http://askubuntu.com/questions/65047/can-no-longer-boot-with-grub2](http://askubuntu.com/questions/65047/can-no-longer-boot-with-grub2))

Daniel- 

What sort of machine is your computer, old or newish?

You bios is recognizing the SSD and the system has placed it to be no1 in the pecking order.

This is probably different to the previous drive arrangement.  Grub 2 can use the UUID identification system for drives, so you need to establish the UUID of your drives.

```
  sudo blkid 
```Then edit Grub 2 using those id's.

This should fix your problem.

Best regards, Tony.

---

### Post by Daniel350 on 2011-10-10
> **vidtek said:**
> Daniel- 

What sort of machine is your computer, old or newish?


Relatively old now, on the old P35 chip set, the CPU actually has to be OC'd to remain stable. haha.

> **vidtek said:**
> 
You bios is recognizing the SSD and the system has placed it to be no1 in the pecking order.

This is probably different to the previous drive arrangement.  Grub 2 can use the UUID identification system for drives, so you need to establish the UUID of your drives.

```
  sudo blkid 
```Then edit Grub 2 using those id's.

This should fix your problem.

Best regards, Tony.

My output of blkid is:

[PHP]/dev/sda1: UUID="b89e91dd-e602-4651-8da2-342a98cb05e4" TYPE="ext4" 
/dev/sda5: UUID="a8548e16-344e-442d-8b7c-e595095604e4" TYPE="swap" 
/dev/sdc1: LABEL="Data" UUID="94CE1194CE11702A" TYPE="ntfs" 
/dev/sdb: LABEL="SData" UUID="435942c7-ec91-4ca3-afaf-cf9ea1716f47" TYPE="ext4"[/PHP]

sda and sdb are the F60 Corsair SSDs, and sdc is a 250G HDD.

What do you mean by edit Grub 2?

My grub.cfg contains [snippet]:
```

...

menuentry 'Ubuntu, with Linux 2.6.38-11-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root b89e91dd-e602-4651-8da2-342a98cb05e4
	linux	/boot/vmlinuz-2.6.38-11-server root=UUID=b89e91dd-e602-4651-8da2-342a98cb05e4 ro   quiet
	initrd	/boot/initrd.img-2.6.38-11-server
}

...

```

Which as far as I can tell, is correct... but my problem is I never get to the GRUB menu, it just errors out as posted, and then goes to the rescue console.
Note this same error occurs when I have NO drives installed in machine... which I never knew could happen? Where exactly does GRUB install...

EDIT:

It appears that switching my BIOS SATA controller from IDE to AHCI resolved the issue... now to figure what they even means lol.

EDIT2:

It now appears that the reason AHCI resolved the issue is because it reset my boot priority and actually gave different names for the drives. As you said, my system decided the new drive was number 1, and was hence booting from it instead of the original; which I had assumed. Although I had tested this by alternating their boot order, there is no way to confirm the switch had occurred as they (previously) had identical names in BIOS.

Thanks for the help.

---

### Post by vidtek on 2011-10-11
> **Daniel350 said:**
> Relatively old now, on the old P35 chip set, the CPU actually has to be OC'd to remain stable. haha.



My output of blkid is:

[PHP]/dev/sda1: UUID="b89e91dd-e602-4651-8da2-342a98cb05e4" TYPE="ext4" 
/dev/sda5: UUID="a8548e16-344e-442d-8b7c-e595095604e4" TYPE="swap" 
/dev/sdc1: LABEL="Data" UUID="94CE1194CE11702A" TYPE="ntfs" 
/dev/sdb: LABEL="SData" UUID="435942c7-ec91-4ca3-afaf-cf9ea1716f47" TYPE="ext4"[/PHP]sda and sdb are the F60 Corsair SSDs, and sdc is a 250G HDD.

What do you mean by edit Grub 2?

My grub.cfg contains [snippet]:
```

...

menuentry 'Ubuntu, with Linux 2.6.38-11-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root b89e91dd-e602-4651-8da2-342a98cb05e4
    linux    /boot/vmlinuz-2.6.38-11-server root=UUID=b89e91dd-e602-4651-8da2-342a98cb05e4 ro   quiet
    initrd    /boot/initrd.img-2.6.38-11-server
}

...

```Which as far as I can tell, is correct... but my problem is I never get to the GRUB menu, it just errors out as posted, and then goes to the rescue console.
Note this same error occurs when I have NO drives installed in machine... which I never knew could happen? Where exactly does GRUB install...

EDIT:

It appears that switching my BIOS SATA controller from IDE to AHCI resolved the issue... now to figure what they even means lol.

EDIT2:

It now appears that the reason AHCI resolved the issue is because it reset my boot priority and actually gave different names for the drives. As you said, my system decided the new drive was number 1, and was hence booting from it instead of the original; which I had assumed. Although I had tested this by alternating their boot order, there is no way to confirm the switch had occurred as they (previously) had identical names in BIOS.

Thanks for the help.

Changing from IDE to AHCI or RAID in the bios will also allow older cloning programmes such as Acronis 11 to work as well.  These programmes wouldn't recognize the drives.

Now you have Grub 2 working, you can fine tune fstab and replace the /dev/sdxx with the UUID's for each drive.  remove the quote marks and cut and paste.

Tony.

---

