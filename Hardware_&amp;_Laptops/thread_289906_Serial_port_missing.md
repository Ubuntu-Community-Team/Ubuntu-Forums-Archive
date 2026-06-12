---
title: "Serial port missing"
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by gungner on 2006-10-31
Hi, I just moved away from Mandriva2006 into i386 Server 6.06LTS on a Via EPIA cl6000 with four serial ports which worked like a dream on Mandriva. On Ubuntu only ttyS0 works :(

root@fw# ll /dev/ttyS*
0 crw-rw---- 1 root dialout 4,  64 2006-10-31 19:31 /dev/ttyS0
0 crw-rw---- 1 root dialout 4,  65 2006-10-31 19:31 /dev/ttyS1
0 crw-rw---- 1 root dialout 4,  74 2006-10-31 19:31 /dev/ttyS10
0 crw-rw---- 1 root dialout 4,  75 2006-10-31 19:31 /dev/ttyS11
0 crw-rw---- 1 root dialout 4,  76 2006-10-31 19:31 /dev/ttyS12
0 crw-rw---- 1 root dialout 4,  77 2006-10-31 19:31 /dev/ttyS13
0 crw-rw---- 1 root dialout 4,  78 2006-10-31 19:31 /dev/ttyS14
0 crw-rw---- 1 root dialout 4,  79 2006-10-31 19:31 /dev/ttyS15
0 crw-rw---- 1 root dialout 4,  80 2006-10-31 19:31 /dev/ttyS16
0 crw-rw---- 1 root dialout 4,  81 2006-10-31 19:31 /dev/ttyS17
0 crw-rw---- 1 root dialout 4,  82 2006-10-31 19:31 /dev/ttyS18
0 crw-rw---- 1 root dialout 4,  83 2006-10-31 19:31 /dev/ttyS19
0 crw-rw---- 1 root dialout 4,  66 2006-10-31 19:31 /dev/ttyS2
0 crw-rw---- 1 root dialout 4,  84 2006-10-31 19:31 /dev/ttyS20
0 crw-rw---- 1 root dialout 4,  85 2006-10-31 19:31 /dev/ttyS21
0 crw-rw---- 1 root dialout 4,  86 2006-10-31 19:31 /dev/ttyS22
0 crw-rw---- 1 root dialout 4,  87 2006-10-31 19:31 /dev/ttyS23
0 crw-rw---- 1 root dialout 4,  88 2006-10-31 19:31 /dev/ttyS24
0 crw-rw---- 1 root dialout 4,  89 2006-10-31 19:31 /dev/ttyS25
0 crw-rw---- 1 root dialout 4,  90 2006-10-31 19:31 /dev/ttyS26
0 crw-rw---- 1 root dialout 4,  91 2006-10-31 19:31 /dev/ttyS27
0 crw-rw---- 1 root dialout 4,  92 2006-10-31 19:31 /dev/ttyS28
0 crw-rw---- 1 root dialout 4,  93 2006-10-31 19:31 /dev/ttyS29
0 crw-rw---- 1 root dialout 4,  67 2006-10-31 19:31 /dev/ttyS3
0 crw-rw---- 1 root dialout 4,  94 2006-10-31 19:31 /dev/ttyS30
0 crw-rw---- 1 root dialout 4,  95 2006-10-31 19:31 /dev/ttyS31
0 crw-rw---- 1 root dialout 4,  96 2006-10-31 19:31 /dev/ttyS32
0 crw-rw---- 1 root dialout 4,  97 2006-10-31 19:31 /dev/ttyS33
0 crw-rw---- 1 root dialout 4,  98 2006-10-31 19:31 /dev/ttyS34
0 crw-rw---- 1 root dialout 4,  99 2006-10-31 19:31 /dev/ttyS35
0 crw-rw---- 1 root dialout 4, 100 2006-10-31 19:31 /dev/ttyS36
0 crw-rw---- 1 root dialout 4, 101 2006-10-31 19:31 /dev/ttyS37
0 crw-rw---- 1 root dialout 4, 102 2006-10-31 19:31 /dev/ttyS38
0 crw-rw---- 1 root dialout 4, 103 2006-10-31 19:31 /dev/ttyS39
0 crw-rw---- 1 root dialout 4,  68 2006-10-31 19:31 /dev/ttyS4
0 crw-rw---- 1 root dialout 4, 104 2006-10-31 19:31 /dev/ttyS40
0 crw-rw---- 1 root dialout 4, 105 2006-10-31 19:31 /dev/ttyS41
0 crw-rw---- 1 root dialout 4, 106 2006-10-31 19:31 /dev/ttyS42
0 crw-rw---- 1 root dialout 4, 107 2006-10-31 19:31 /dev/ttyS43
0 crw-rw---- 1 root dialout 4, 108 2006-10-31 19:31 /dev/ttyS44
0 crw-rw---- 1 root dialout 4, 109 2006-10-31 19:31 /dev/ttyS45
0 crw-rw---- 1 root dialout 4, 110 2006-10-31 19:31 /dev/ttyS46
0 crw-rw---- 1 root dialout 4, 111 2006-10-31 19:31 /dev/ttyS47
0 crw-rw---- 1 root dialout 4,  69 2006-10-31 19:31 /dev/ttyS5
0 crw-rw---- 1 root dialout 4,  70 2006-10-31 19:31 /dev/ttyS6
0 crw-rw---- 1 root dialout 4,  71 2006-10-31 19:31 /dev/ttyS7
0 crw-rw---- 1 root dialout 4,  72 2006-10-31 19:31 /dev/ttyS8
0 crw-rw---- 1 root dialout 4,  73 2006-10-31 19:31 /dev/ttyS9

Is it not strange that there is only one row on ttyS0 (which work) and 1-3 got several rows? switching back to my HD with Mandriva on shows only one row for each port and all works. Why is this?

root@fw# dmesg|grep ttyS
[17179575.992000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179575.992000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179575.992000] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[17179575.992000] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[17179576.000000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179576.000000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179576.000000] 00:0d: ttyS2 at I/O 0x3e8 (irq = 5) is a 16550A
[17179576.000000] 00:0e: ttyS3 at I/O 0x2e8 (irq = 10) is a 16550A

It look OK to me, no chared IRQ on any port, and address is correct.

root@fw# cat /proc/interrupts
           CPU0
  0:     223606          XT-PIC  timer
  1:         84          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  7:          4          XT-PIC  parport0
  8:          4          XT-PIC  rtc
  9:          0          XT-PIC  acpi
 11:      78685          XT-PIC  ehci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb4, eth0, eth1, VIA8233
 12:         96          XT-PIC  i8042
 14:       3640          XT-PIC  ide0
 15:         76          XT-PIC  ide1
NMI:          0
LOC:          0
ERR:          0
MIS:          0

Why don't I see any IRQ used here?

please any one, I want to stick with Ubuntu (allready using Debian on several SLUGS) but I need to get a hang of how to get back my four serial port. Thanks

//Tord

---

### Post by RFScheer on 2006-11-27
Did you get 4 ports working?  I have a similar system coming in the mail and need the 4 ports for robot control.

---

### Post by gungner on 2006-11-28
yes, it does. I still got all those strange ttyS1n etc, etc, bu as long I stick to only ttyS1 it works.

all the luck /Tord

---

### Post by RFScheer on 2006-11-29
Thx.  BTW the listing of ports doesn't look strange, really, it's just an alphabetical rather than numerical-order listing of xxx0 through xxx47.

---

