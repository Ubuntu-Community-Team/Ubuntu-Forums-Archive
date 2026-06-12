---
title: "Sony VAIO S and EFI troubles"
date: 2012-06-12
forum: Hardware
---

### Post by rohandhruva on 2012-06-12
I bought a new Sony Vaio S series laptop. It uses Insyde H2O BIOS EFI, and trying to install Linux on it is driving me crazy.

```

root@kubuntu:~# parted /dev/sda print
Model: ATA Hitachi HTS72756 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  274MB   273MB   fat32        EFI system partition          hidden
 2      274MB   20.8GB  20.6GB  ntfs         Basic data partition          hidden, diag
 3      20.8GB  21.1GB  273MB   fat32        EFI system partition          boot
 4      21.1GB  21.3GB  134MB                Microsoft reserved partition  msftres
 5      21.3GB  342GB   320GB   ntfs         Basic data partition
 6      342GB   358GB   16.1GB  ext4         Basic data partition
 7      358GB   374GB   16.1GB  ntfs         Basic data partition
 8      374GB   640GB   266GB   ntfs         Basic data partition

```

What is surprising is that there are 2 EFI system partitions on the disk. The sda2 partition is a 20gb recovery partition which loads windows with a basic recovery interface. This is accessible by pressing the "ASSIST" button as opposed to the normal power button. I presume that the sda1 EFI System Partition (ESP) loads into this recovery. 

The sda3 ESP has more fleshed out entries for Microsoft Windows, which actually goes into Windows 7 (as confirmed by bcdedit.exe on Windows). Ubuntu is installed on sda6, and while installation I chose sda3 as my boot partition. The installer correctly created a sda3/EFI/ubuntu/grubx64.efi application.

The real problem: for the life of me, I can't set it to be the default! I tried creating a sda3/startup.nsh which called grubx64.efi, but it didn't help -- on rebooting, the system still boots into windows. I tried using efibootmgr, and that shows as it it worked:

```


root@kubuntu:~# efibootmgr 
BootCurrent: 0000
BootOrder: 0000,0001
Boot0000* EFI USB Device
Boot0001* Windows Boot Manager
root@kubuntu:~# efibootmgr --create --gpt --disk /dev/sda --part 3 --write-signature --label "GRUB2" --loader "\\EFI\\ubuntu\\grubx64.efi" 
BootCurrent: 0000
BootOrder: 0002,0000,0001
Boot0000* EFI USB Device
Boot0001* Windows Boot Manager
Boot0002* GRUB2
root@kubuntu:~# efibootmgr
BootCurrent: 0000
BootOrder: 0002,0000,0001
Boot0000* EFI USB Device
Boot0001* Windows Boot Manager
Boot0002* GRUB2

```

However, on rebooting, as you guessed, the machine rebooted directly back into Windows. 

The only things I can think of are:
1. The sda1 partition is somehow being used
2. Overwrite /EFI/Boot/bootx64.efi and /EFI/Microsoft/Boot/bootmgfw.efi with grubx64.efi [but this seems really radical]. 

Can anyone please help me out? Thanks -- any help is greatly appreciated, as this issue is driving me crazy! :confused:

---

