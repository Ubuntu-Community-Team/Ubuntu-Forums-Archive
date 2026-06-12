---
title: "Help Repartitioning &amp; Help With WINE [Seperate Problems]"
date: 2010-06-20
forum: Hardware
---

### Post by SuperHumanly on 2010-06-20
Alright, i've got 2 issues, figured i'd make them into 1 thread.


First problem, i'm trying to resize my Data "/dev/sda3" to take up the unallocated space. In other words, resize the Data partition to 310GB, but i'm not able to just "resize" the Data partition, even using GParted LiveCD....any ideas?







Also, having issues with WINE trying to run iTunes (but the issue seems to be somewhat urelated to iTunes)

Here's the error i'm getting:

```

chris@chris-laptop:~$ cd "/home/chris/.wine/drive_c/Program Files/iTunes"
chris@chris-laptop:~/.wine/drive_c/Program Files/iTunes$ wine iTunes
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:service:EnumServicesStatusW 0x13e828 type=30 state=3 (nil) 0 0x78e7e8 0x78e7f4 0x78e7f0
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x78e5f8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x139d40,(nil)): stub
fixme:netapi32:NetGetJoinInformation Stub (null) 0x78e688 0x78e690
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:service:QueryServiceConfig2W Level 6 not implemented
fixme:service:QueryServiceConfig2W Level 6 not implemented
chris@chris-laptop:~/.wine/drive_c/Program Files/iTunes$ 

```

---

### Post by Mark Phelps on 2010-06-21
> **SuperHumanly said:**
> Alright, i've got 2 issues, figured i'd make them into 1 thread.

Bad idea ... as they are totally unrelated problems ...

As to iTunes, the link below is to the iTunes page on the WineHQ site, and as you can see, the ratings are really quite bad:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347")

Post the second issue in the Wine subforum.  You will get faster responses there.  

> First problem, i'm trying to resize my Data "/dev/sda3" to take up the unallocated space. In other words, resize the Data partition to 310GB, but i'm not able to just "resize" the Data partition, even using GParted LiveCD....any ideas?

Not mind readers here ... post the results of "sudo fdisk -lu" (that's a lowercase L, not a one).







Also, having issues with WINE trying to run iTunes (but the issue seems to be somewhat urelated to iTunes)

Here's the error i'm getting:

```

chris@chris-laptop:~$ cd "/home/chris/.wine/drive_c/Program Files/iTunes"
chris@chris-laptop:~/.wine/drive_c/Program Files/iTunes$ wine iTunes
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:service:EnumServicesStatusW 0x13e828 type=30 state=3 (nil) 0 0x78e7e8 0x78e7f4 0x78e7f0
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x78e5f8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x139d40,(nil)): stub
fixme:netapi32:NetGetJoinInformation Stub (null) 0x78e688 0x78e690
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:service:QueryServiceConfig2W Level 6 not implemented
fixme:service:QueryServiceConfig2W Level 6 not implemented
chris@chris-laptop:~/.wine/drive_c/Program Files/iTunes$ 

```[/QUOTE]

---

### Post by SuperHumanly on 2010-06-21
Sorry about that, pretty new to using Ubuntu, tried to give as much info as I could :)

```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5cdf8c95

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          208845   178482149    89136652+  83  Linux
/dev/sda3       215319195   625139711   204910258+   7  HPFS/NTFS
/dev/sda4       178485246   215318527    18416641    5  Extended
/dev/sda5       178485248   213688319    17601536   83  Linux
/dev/sda6       213690368   215318527      814080   82  Linux swap / Solaris

Partition table entries are not in disk order

```

There ya go :]

---

