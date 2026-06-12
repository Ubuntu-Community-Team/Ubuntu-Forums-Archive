---
title: "Supermicro x9dri-f + LSI SAS 9201-16i does not see disks"
date: 2022-01-23
forum: Hardware
---

### Post by blood-mce on 2022-01-23
Sorry for english google translate)


Probably, we should start with the fact that two windows 10 + ubuntu 20.04 are installed so that there would be no suspicion that something is not working)
The essence of the problem is such a server with a Supermicro x9dri-f motherboard and an LSI SAS 9201-16i controller in the HBA.
I boot into Windows, everything works, it sees all the disks and in any expander slot, I boot into ubuntu and silence is below the proof


The controller is...
```

blood@server:~$ lspci -s 00
00:00.0 Host bridge: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 DMI2 (rev 04)
02:00.0 Ethernet controller: Intel Corporation I350 Gigabit Network Connection (rev 01)
02:00.1 Ethernet controller: Intel Corporation I350 Gigabit Network Connection (rev 01)
06:00.0 Serial Attached SCSI controller: Broadcom / LSI SAS2116 PCI-Express Fusion-MPT SAS-2 [Meteor] (rev 02)
07:00.0 Serial Attached SCSI controller: Intel Corporation C602 chipset 4-Port SATA Storage Control Unit (rev 06)
80:00.0 PCI bridge: Intel Corporation Xeon E7 v2/Xeon E5 v2/Core i7 PCI Express Root Port in DMI2 Mode (rev 04)
82:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller 172Xa/172Xb (rev 01)

```


Everything seems to be in order...
```

blood@server:~$ lspci -vd 1000:0064
06:00.0 Serial Attached SCSI controller: Broadcom / LSI SAS2116 PCI-Express Fusion-MPT SAS-2 [Meteor] (rev 02)
        Subsystem: Broadcom / LSI SAS 9201-16i
        Flags: bus master, fast devsel, latency 0, IRQ 44, NUMA node 0
        I/O ports at 7000 [size=256]
        Memory at dfb9c000 (64-bit, non-prefetchable) [size=16K]
        Memory at dfb40000 (64-bit, non-prefetchable) [size=256K]
        Expansion ROM at df900000 [disabled] [size=512K]
        Capabilities: <access denied>
        Kernel driver in use: mpt3sas
        Kernel modules: mpt3sas

```


But there is no disc...
```

blood@server:~$ sudo fdisk -l
[sudo] &#1087;&#1072;&#1088;&#1086;&#1083;&#1100; &#1076;&#1083;&#1103; blood:
&#1044;&#1080;&#1089;&#1082; /dev/loop0: 55,45 MiB, 58130432 &#1073;&#1072;&#1081;&#1090;, 113536 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074;
&#1045;&#1076;&#1080;&#1085;&#1080;&#1094;&#1099;: &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074; &#1087;&#1086; 1 * 512 = 512 &#1073;&#1072;&#1081;&#1090;
&#1056;&#1072;&#1079;&#1084;&#1077;&#1088; &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1072; (&#1083;&#1086;&#1075;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081;/&#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081;): 512 &#1073;&#1072;&#1081;&#1090; / 512 &#1073;&#1072;&#1081;&#1090;
&#1056;&#1072;&#1079;&#1084;&#1077;&#1088; I/O (&#1084;&#1080;&#1085;&#1080;&#1084;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081;/&#1086;&#1087;&#1090;&#1080;&#1084;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081;): 512 &#1073;&#1072;&#1081;&#1090; / 512 &#1073;&#1072;&#1081;&#1090;




&#1044;&#1080;&#1089;&#1082; /dev/loop1: 219 MiB, 229638144 &#1073;&#1072;&#1081;&#1090;, 448512 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074;
&#1045;&#1076;&#1080;&#1085;&#1080;&#1094;&#1099;: &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074; &#1087;&#1086; 1 * 512 = 512 &#1073;&#1072;&#1081;&#1090;
&#1056;&#1072;&#1079;&#1084;&#1077;&#1088; &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1072; (&#1083;&#1086;&#1075;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081;/&#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081;): 512 &#1073;&#1072;&#1081;&#1090; / 512 &#1073;&#1072;&#1081;&#1090;
&#1056;&#1072;&#1079;&#1084;&#1077;&#1088; I/O (&#1084;&#1080;&#1085;&#1080;&#1084;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081;/&#1086;&#1087;&#1090;&#1080;&#1084;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081;): 512 &#1073;&#1072;&#1081;&#1090; / 512 &#1073;&#1072;&#1081;&#1090;




&#1044;&#1080;&#1089;&#1082; /dev/loop2: 50,98 MiB, 53432320 &#1073;&#1072;&#1081;&#1090;, 104360 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074;
&#1045;&#1076;&#1080;&#1085;&#1080;&#1094;&#1099;: &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074; &#1087;&#1086; 1 * 512 = 512 &#1073;&#1072;&#1081;&#1090;
&#1056;&#1072;&#1079;&#1084;&#1077;&#1088; &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1072; (&#1083;&#1086;&#1075;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081;/&#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081;): 512 &#1073;&#1072;&#1081;&#1090; / 512 &#1073;&#1072;&#1081;&#1090;
&#1056;&#1072;&#1079;&#1084;&#1077;&#1088; I/O (&#1084;&#1080;&#1085;&#1080;&#1084;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081;/&#1086;&#1087;&#1090;&#1080;&#1084;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081;): 512 &#1073;&#1072;&#1081;&#1090; / 512 &#1073;&#1072;&#1081;&#1090;




&#1044;&#1080;&#1089;&#1082; /dev/loop3: 65,1 MiB, 68259840 &#1073;&#1072;&#1081;&#1090;, 133320 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074;
&#1045;&#1076;&#1080;&#1085;&#1080;&#1094;&#1099;: &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074; &#1087;&#1086; 1 * 512 = 512 &#1073;&#1072;&#1081;&#1090;
&#1056;&#1072;&#1079;&#1084;&#1077;&#1088; &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1072; (&#1083;&#1086;&#1075;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081;/&#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081;): 512 &#1073;&#1072;&#1081;&#1090; / 512 &#1073;&#1072;&#1081;&#1090;
&#1056;&#1072;&#1079;&#1084;&#1077;&#1088; I/O (&#1084;&#1080;&#1085;&#1080;&#1084;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081;/&#1086;&#1087;&#1090;&#1080;&#1084;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081;): 512 &#1073;&#1072;&#1081;&#1090; / 512 &#1073;&#1072;&#1081;&#1090;




&#1044;&#1080;&#1089;&#1082; /dev/loop4: 32,3 MiB, 33865728 &#1073;&#1072;&#1081;&#1090;, 66144 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074;
&#1045;&#1076;&#1080;&#1085;&#1080;&#1094;&#1099;: &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074; &#1087;&#1086; 1 * 512 = 512 &#1073;&#1072;&#1081;&#1090;
&#1056;&#1072;&#1079;&#1084;&#1077;&#1088; &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1072; (&#1083;&#1086;&#1075;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081;/&#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081;): 512 &#1073;&#1072;&#1081;&#1090; / 512 &#1073;&#1072;&#1081;&#1090;
&#1056;&#1072;&#1079;&#1084;&#1077;&#1088; I/O (&#1084;&#1080;&#1085;&#1080;&#1084;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081;/&#1086;&#1087;&#1090;&#1080;&#1084;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081;): 512 &#1073;&#1072;&#1081;&#1090; / 512 &#1073;&#1072;&#1081;&#1090;




&#1044;&#1080;&#1089;&#1082; /dev/nvme0n1: 2,93 TiB, 3200631791616 &#1073;&#1072;&#1081;&#1090;, 6251233968 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074;
Disk model: SAMSUNG MZPLL3T2HAJQ-00005
&#1045;&#1076;&#1080;&#1085;&#1080;&#1094;&#1099;: &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074; &#1087;&#1086; 1 * 512 = 512 &#1073;&#1072;&#1081;&#1090;
&#1056;&#1072;&#1079;&#1084;&#1077;&#1088; &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1072; (&#1083;&#1086;&#1075;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081;/&#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081;): 512 &#1073;&#1072;&#1081;&#1090; / 512 &#1073;&#1072;&#1081;&#1090;
&#1056;&#1072;&#1079;&#1084;&#1077;&#1088; I/O (&#1084;&#1080;&#1085;&#1080;&#1084;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081;/&#1086;&#1087;&#1090;&#1080;&#1084;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081;): 512 &#1073;&#1072;&#1081;&#1090; / 512 &#1073;&#1072;&#1081;&#1090;
&#1058;&#1080;&#1087; &#1084;&#1077;&#1090;&#1082;&#1080; &#1076;&#1080;&#1089;&#1082;&#1072;: gpt
&#1048;&#1076;&#1077;&#1085;&#1090;&#1080;&#1092;&#1080;&#1082;&#1072;&#1090;&#1086;&#1088; &#1076;&#1080;&#1089;&#1082;&#1072;: A169278F-XXX-XXX-XXX-XXXXXX7F3D7


&#1059;&#1089;&#1090;&#1088;-&#1074;&#1086;        &#1085;&#1072;&#1095;&#1072;&#1083;&#1086;      &#1050;&#1086;&#1085;&#1077;&#1094;    &#1057;&#1077;&#1082;&#1090;&#1086;&#1088;&#1099; &#1056;&#1072;&#1079;&#1084;&#1077;&#1088; &#1058;&#1080;&#1087;
/dev/nvme0n1p1     34      32767      32734    16M &#1047;&#1072;&#1088;&#1077;&#1079;&#1077;&#1088;&#1074;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1085;&#1099;&#1081; &#1088;&#1072;&#1079;&#1076;&#1077;&#1083; Microsoft
/dev/nvme0n1p2  32768 6251231231 6251198464   2,9T Microsoft basic data




&#1044;&#1080;&#1089;&#1082; /dev/sda: 238,49 GiB, 256060514304 &#1073;&#1072;&#1081;&#1090;, 500118192 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074;
Disk model: SPCC Solid State
&#1045;&#1076;&#1080;&#1085;&#1080;&#1094;&#1099;: &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1086;&#1074; &#1087;&#1086; 1 * 512 = 512 &#1073;&#1072;&#1081;&#1090;
&#1056;&#1072;&#1079;&#1084;&#1077;&#1088; &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1072; (&#1083;&#1086;&#1075;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081;/&#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081;): 512 &#1073;&#1072;&#1081;&#1090; / 512 &#1073;&#1072;&#1081;&#1090;
&#1056;&#1072;&#1079;&#1084;&#1077;&#1088; I/O (&#1084;&#1080;&#1085;&#1080;&#1084;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081;/&#1086;&#1087;&#1090;&#1080;&#1084;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081;): 512 &#1073;&#1072;&#1081;&#1090; / 512 &#1073;&#1072;&#1081;&#1090;
&#1058;&#1080;&#1087; &#1084;&#1077;&#1090;&#1082;&#1080; &#1076;&#1080;&#1089;&#1082;&#1072;: dos
&#1048;&#1076;&#1077;&#1085;&#1090;&#1080;&#1092;&#1080;&#1082;&#1072;&#1090;&#1086;&#1088; &#1076;&#1080;&#1089;&#1082;&#1072;: 0x64c23dfb


&#1059;&#1089;&#1090;&#1088;-&#1074;&#1086;    &#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1086;&#1095;&#1085;&#1099;&#1081;    &#1085;&#1072;&#1095;&#1072;&#1083;&#1086;     &#1050;&#1086;&#1085;&#1077;&#1094;   &#1057;&#1077;&#1082;&#1090;&#1086;&#1088;&#1099; &#1056;&#1072;&#1079;&#1084;&#1077;&#1088; &#1048;&#1076;&#1077;&#1085;&#1090;&#1080;&#1092;&#1080;&#1082;&#1072;&#1090;&#1086;&#1088; &#1058;&#1080;&#1087;
/dev/sda1  *                2048    104447    102400    50M             7 HPFS/NTFS/exFAT
/dev/sda2                 104448 346292028 346187581 165,1G             7 HPFS/NTFS/exFAT
/dev/sda3              346292224 348159999   1867776   912M            27 &#1057;&#1082;&#1088;&#1099;&#1090;&#1099;&#1081; NTFS WinRE
/dev/sda4              348162046 500117503 151955458  72,5G             5 &#1056;&#1072;&#1089;&#1096;&#1080;&#1088;&#1077;&#1085;&#1085;&#1099;&#1081;
/dev/sda5              348162048 349210623   1048576   512M             b W95 FAT32
/dev/sda6              349212672 500117503 150904832    72G            83 Linux

```

```
blood@server:~$ lsscsi -s
[3:0:0:0]    disk    ATA      SPCC Solid State 0A0   /dev/sda    256GB
[N:0:33:1]   disk    SAMSUNG MZPLL3T2HAJQ-00005__1              -          3.20TB

```

Screenshots that in Windows are normal, I'm attaching ...

[[IMG]https://i.ibb.co/sg4WZnq/1.jpg[/IMG]]("https://ibb.co/sg4WZnq") [[IMG]https://i.ibb.co/JsxL0z0/2.jpg[/IMG]]("https://ibb.co/JsxL0z0")

---

### Post by tea for one on 2022-01-23
It is not easy to reply to this thread because the Windows screenshots are not in English.
If you are unfamiliar with the Windows layout, it is very difficult to decipher?

The first Windows screenshot shows 4 drives (or possibly fewer drives with multiple partitions)
Windows has a habit of naming drives when they could be partitions. 

Device nvmeon1 (gpt) has two partitions
Device sda (dos) has six partitions 
Windows screenshot displays four drives/partitions (C: D; E: F: )

Device E: seems to be empty, is this the missing device?

Edit: sda4 extended (according to Google translate from Russian)

---

### Post by oldfred on 2022-01-23
Also not sure, but seeing sda5 as FAT32 which could be an ESP - efi system partition.
If so then Ubuntu may be installed in UEFI boot mode.
But Windows is on a DOS(msdos) partitioned drive, which means Windows must be in old BIOS boot mode, not UEFI boot mode.

Have you updated system UEFI to latest firmware?
And updated SSD/NVMe drive to latest firmware?
Those should be updated even if not using Ubuntu.

---

### Post by blood-mce on 2022-01-23
> **tea for one said:**
> It is not easy to reply to this thread because the Windows screenshots are not in English.
If you are unfamiliar with the Windows layout, it is very difficult to decipher?

The first Windows screenshot shows 4 drives (or possibly fewer drives with multiple partitions)
Windows has a habit of naming drives when they could be partitions. 

Device nvmeon1 (gpt) has two partitions
Device sda (dos) has six partitions 
Windows screenshot displays four drives/partitions (C: D; E: F: )

Device E: seems to be empty, is this the missing device?

Edit: sda4 extended (according to Google translate from Russian)

So it will be clear what is not?
[[IMG]https://i.ibb.co/xJnC2Mm/3.jpg[/IMG]]("https://ibb.co/xJnC2Mm")

---

### Post by blood-mce on 2022-01-23
> **oldfred said:**
> Also not sure, but seeing sda5 as FAT32 which could be an ESP - efi system partition.
If so then Ubuntu may be installed in UEFI boot mode.
But Windows is on a DOS(msdos) partitioned drive, which means Windows must be in old BIOS boot mode, not UEFI boot mode.

Have you updated system UEFI to latest firmware?
And updated SSD/NVMe drive to latest firmware?
Those should be updated even if not using Ubuntu.

loading legacy, uefi is not used!

---

### Post by tea for one on 2022-01-23
disk_60 (device D: ) is missing.

Can you supply more information?

What is the device?
External/internal?
How is it connected?
Is it encrypted?

---

### Post by blood-mce on 2022-01-23
> **tea for one said:**
> disk_60 (device D: ) is missing.
Yes
> **tea for one said:**
> What is the device?
HDD Sata TOSHIBA MG07ACA10103 (Any hdd seagate, wd sata / sas exos 10, 12, 14, 18 Tb does not see)> **tea for one said:**
> External/internal?
internal
> **tea for one said:**
> How is it connected?
Supermicro x9dri-f -> LSI SAS 9201-16i (inserted in PCI-e 3.0 x8) -> SuperMicro BPN-SAS2-846EL2 Backplane (connected to the adapter by two SFF-8087 to SFF-8087) -> 14Tb TOSHIBA MG07ACA10103 
> **tea for one said:**
> Is it encrypted?
No

---

### Post by Autodave on 2022-01-23
Just a thought.....did you turn off "fast boot"?  If not, Windows is holding those drives hostage.  And, if those are partitions instead of drives, that could be the problem.

---

### Post by blood-mce on 2022-01-24
Solved the problem. solution below)
Changed HBA LSI 9201-16i to LSI 9211-4i and it worked right away. Thus I understood that the matter was in the controller and began to dig in this direction. I twisted all the available settings and realized that it was not about them. Decided to update bios and Firmware LSI 9201 - 16i. Here is a step-by-step guide for someone who might find it useful:
1. We go to the broadcom website and download two archives 9201-16i_Package_P20_IT_FW_BIOS_for_MSDOS_Windows and Installer_P20_for_UEFI, take files from them and throw them into one folder:
```
sas2flash_efi_ebc_rel/sas2flash.efi
sasbios_rel/mptsas2.rom
Firmware/HBA_9201_16i_IT/9201-16i_it.bin
```
2. We go into the BIOS and set the UEFI boot as the boot disk, select the EFI console
3. After loading it, enter mode and see the modes available for the console resolution (this is done in order to see more lines)
```
mode 100 31
``` 
4. Next, enter map and look for the FSx device on the USB bus in the list, enter for example 
```
FS2:\
```
5. With the ls commands, we look at the folders and go into it with the cd command
6. See if there is a controller in the system:
```
sas2flash.efi -listall
```
7. Specify to flash FW and Bios
```
sas2flash.efi -o -f 9201-16i_it.bin -b MPTSAS2.ROM
```
8. We reboot and see all the disks now in linux and windows I had firmware 13, apparently because of it there was such a bug (
P.S. Good luck to everyone)
[[IMG]https://i.ibb.co/5B8DBVb/2022-01-24-20-51-04.jpg[/IMG]]("https://ibb.co/5B8DBVb") [[IMG]https://i.ibb.co/zVX5pr5/2022-01-24-21-51-05.jpg[/IMG]]("https://ibb.co/zVX5pr5")

---

### Post by tea for one on 2022-01-24
Well, congratulations.

Not only a difficult problem but also a complicated solution.
Far exceeds my level of knowledge.

Here is how to mark the thread as solved [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

