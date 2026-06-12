---
title: "Computer freezes when copy data from DVD-RW drive, also when trying to make an ISO"
date: 2008-06-04
forum: Hardware
---

### Post by carlosalvatore on 2008-06-04
Greetings... Computer freezes when copy data from DVD-RW drive, also when trying to make an ISO

First of all the hardware:
```
MB AK77-400N (VIA KT400N NB & VIA 8235 SB)
AMD Athlon XP 2000+ (~1.67Hz)
RAM DDR 1.7 GB ~ 266 MHz (Two PC3200 (1024 and 512 MB) and one PC2100 (256 MB) Modules)
AGP 8x nVidia GeForce MX 4000 128MB
HD ATAPI IDE 80 GB MASTER (sda1=File System 55.4 GB + sda3=ext3 /home 14.8 GB + sda2=swap 3.72 GB)
HD ATAPI IDE 120 GB SLAVE (sdb1=ext3 100GB + sdb2=ext3 11.79 GB)
DVD-RAM LG (HL-DT-ST DVD-RAM GSA-H55N)

```
It happens all the time, I'm using Nero Linux and the problem persists.
I've disabled acpi support, test with and without the nVidia driver.

Any advise will be of help. Thank you.

* When starting Nero Linux, i receive the following message:

Some of your devices are not accessible
Please check that you have the correct permissions on the corresponding devices files.
Nero Linux cannot get access to the following devices:
[QUOTE="Nero Linux"]/dev/sg0 (SCSI Generic Device)
/dev/sg1 (SCSI Generic Device)
[/QUOTE]
I have ATAPI IDE Hard disks, but Ubuntu Hardy doesn't use /dev/hdx blocks anymore it uses /dev/sdx.
here is my fstab file:

[QUOTE="/etc/fstab"]# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=316dc536-4bc6-490c-bb81-0040187144bf / ext3 relatime,errors=remount-ro 0 1
# /dev/sda3
UUID=d1d58add-2597-4b2e-a6b9-deb5f29f5ebb /home ext3 relatime 0 2
# /dev/sdb1
UUID=2ca9b2e4-ec72-4229-9097-8faa9cd38706 /home/carlosalvatore/mydocuments ext3 relatime 0 2
# /dev/sdb2
UUID=d13eb24e-7e62-48dc-a7cb-8dd8e3d5d77a /home/carlosalvatore/mygames ext3 relatime 0 2
# /dev/sda2
UUID=de301d73-c94a-a483-9119-1be5bb318aa6 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
[/QUOTE]

Also here is my /proc/interrupts

```
$ cat /proc/interrupts
           CPU0
  0: 62208 XT-PIC-XT timer
  1: 241 XT-PIC-XT i8042
  2: 0 XT-PIC-XT cascade
  3: 1 XT-PIC-XT
  4: 1 XT-PIC-XT
  5: 0 XT-PIC-XT MPU401 UART
  7: 5 XT-PIC-XT parport0
  8: 3 XT-PIC-XT rtc
  9: 1 XT-PIC-XT acpi
 10: 24847 XT-PIC-XT uhci_hcd:usb1, ehci_hcd:usb4, nvidia
 11: 4169 XT-PIC-XT uhci_hcd:usb2, uhci_hcd:usb3, VIA8233, eth0
 12: 12730 XT-PIC-XT i8042
 14: 15704 XT-PIC-XT libata
 15: 2661 XT-PIC-XT libata
NMI: 0 Non-maskable interrupts
LOC: 0 Local timer interrupts
RES: 0 Rescheduling interrupts
CAL: 0 function call interrupts
TLB: 0 TLB shootdowns
TRM: 0 Thermal event interrupts
SPU: 0 Spurious interrupts
ERR: 0
MIS: 0
```

When using Gutsy DVD reads and write perfect...But in Hardy I'm having this problem. I've also tried copying data directly without Nero Linux. The problem happens even when installing software from DVD drive.

Any advice will be of help. Thank you!

---

### Post by carlosalvatore on 2008-06-30
I finally fix it... you won't believe it, the problem was the IDE Ultra ATA 80 Cable, it was damaged I think.

First i used a 40 wires cable, but the freezes continued, so I bought today a new 80 wires cable, and everything works beautifully.

Thanks to everybody. I hope that anyone having this problem would be able to solve it by reading this post.

---

### Post by carlosalvatore on 2008-12-25
I fixed the problem by compiling and installing my own kernel without the scsi emulation

---

