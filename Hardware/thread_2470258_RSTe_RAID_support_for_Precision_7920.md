---
title: "RSTe RAID support for Precision 7920"
date: 2021-12-23
forum: Hardware
---

### Post by isanaud on 2021-12-23
Hello
I have a Precision 7920 computer which officially supports Ubunutu.
It was also delivered with this distribution installed.
It is unfortunately provided with an intel RSTE raid functionality.
After an update my two disks are asynchronous as you can see below.

Should I have to reinstall the server ? If I reinstall it, how should I manage this raid configuration ?

***[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"***
EFI boot on HDD

[I]** lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"**
[/I]NAME   MOUNTPOINT                   LABEL   SIZE FSTYPE          UUID                                 PARTUUID
sda                                         477G                                                      
&#9500;&#9472;sda1                                      600M vfat            F00D-6429                            0dffd0b1-735a-4d2b-9092-2eff0223378f
&#9500;&#9472;sda2                                        1G ext4            f3b3eeba-b9dd-4db4-96f6-55af238ecf28 2b55caae-43fc-4fb2-8aca-9c624422623c
&#9500;&#9472;sda3                                    471,4G ext4            29b826d5-78b1-442b-8b75-03cb31cb690f d4b579cb-01e3-432d-9d94-1d79228ca459
&#9492;&#9472;sda4                                        4G swap            3341bdef-7e60-4ac2-bc6a-c3b9667d448f 028f16eb-1396-42a1-9590-aa20f43b5c78
sdb                                         477G isw_raid_member                                      
&#9500;&#9472;sdb1                                      600M vfat            F00D-6429                            0dffd0b1-735a-4d2b-9092-2eff0223378f
&#9500;&#9472;sdb2                                        1G ext4            f3b3eeba-b9dd-4db4-96f6-55af238ecf28 2b55caae-43fc-4fb2-8aca-9c624422623c
&#9500;&#9472;sdb3 /                                    447G ext4            29b826d5-78b1-442b-8b75-03cb31cb690f d4b579cb-01e3-432d-9d94-1d79228ca459
&#9492;&#9472;sdb4                                        4G swap            3341bdef-7e60-4ac2-bc6a-c3b9667d448f 028f16eb-1396-42a1-9590-aa20f43b5c78

[I]**cat /etc/fstab **
[/I]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/isw_dfiejchajc_Volume0p3 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_dfiejchajc_Volume0p2 /boot           ext4    defaults        0       2
/dev/mapper/isw_dfiejchajc_Volume0p1 /boot/efi       vfat    umask=0077      0       1
/dev/mapper/isw_dfiejchajc_Volume0p4 none            swap    sw              0       0
/dev/mapper/isw_dfiejchajc_Volume0p4 none            swap    sw              0       0[I]


**lshw |grep -i raid**[/I]

        *-raid
             description: RAID bus controller
             produit: C600/X79 series chipset SATA RAID Controller
             fonctionnalités: raid msi pm bus_master cap_list
     *-raid:0
          description: RAID bus controller
          produit: Volume Management Device NVMe RAID Controller
          fonctionnalités: raid msix pm bus_master cap_list
     *-raid:1
          description: RAID bus controller
          produit: Volume Management Device NVMe RAID Controller
          fonctionnalités: raid msix pm bus_master cap_list

---

