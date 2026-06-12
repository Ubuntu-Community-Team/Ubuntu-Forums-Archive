---
title: "Ubuntu 64bit sees only 3GB of RAM out from 4GB"
date: 2012-03-18
forum: Hardware
---

### Post by aneganov on 2012-03-18
Hi!

Recently I've installed 2x2GB of RAM into my laptop Acer 5930G.
At BIOS POST it shows 4094MB:

[IMG]http://img35.imageshack.us/img35/7678/20120318014236523.jpg[/IMG]

but in Ubuntu I get these values:


```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          3013       2936         76          0         70       1702
-/+ buffers/cache:       1163       1849
Swap:         9536          0       9536
```


```
$ free -g
             total       used       free     shared    buffers     cached
Mem:             2          2          0          0          0          1
-/+ buffers/cache:          1          1
Swap:            9          0          9
```

First - what exactly free -g shows and why only 2?
Second - why it shows 3013 and not 4094? 

lspci output:

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GT] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 16)
03:00.0 Network controller: Intel Corporation WiFi Link 5100

```

System is:

```
$ uname -a
Linux alpha 3.0.0-16-server #29-Ubuntu SMP Tue Feb 14 13:08:12 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

**UPD**

Also, Memtest sees only 3067MB:

[IMG]http://img36.imageshack.us/img36/3851/20120318171147149.jpg[/IMG]


How can I get my 1GB back?

---

### Post by siepo on 2012-03-18
I do know that it is a limitation of some motherboards that they do not make the full 4GB available to the system.

But I don't know whether that is our problem.

---

### Post by aneganov on 2012-03-18
> **siepo said:**
> I do know that it is a limitation of some motherboards that they do not make the full 4GB available to the system.

But I don't know whether that is our problem.

I believe in this case it would message about this at BIOS POST.

---

### Post by aneganov on 2012-03-18
Added photo from memtest86 (the first post)

---

### Post by 2F4U on 2012-03-18
You will never get the full 4 GB. A certain amount of memory gets used by other hardware components as I/O area. If you have an integrated graphics card without it own memory, that will also reduce the memory available to the operating system.

---

### Post by 3Miro on 2012-03-18
For older Motherboard, you have to enable memory "remapping" to allow for the full 4GB to be visible. Newer mobos have that enabled by default.

Also, you will probably get less then 4G as the BIOS gets some for itself. I have 3962/4096 and this is with dedicated graphics.

---

### Post by aneganov on 2012-03-18
> **2F4U said:**
> You will never get the full 4 GB. A certain amount of memory gets used by other hardware components as I/O area. If you have an integrated graphics card without it own memory, that will also reduce the memory available to the operating system.

I have nvidia 9600 gt, which is not onboard, and has its own 512 ram. How can i know what hardware uses my lost 1gb and how to get mem back?

---

### Post by 2F4U on 2012-03-18
It is possible that while your processor may support the memory, your chipset is the limiting factor. 

[http://reviews.cnet.com/8301-13727_7-10327594-263.html?tag=mfiredir](http://reviews.cnet.com/8301-13727_7-10327594-263.html?tag=mfiredir)
[http://en.wikipedia.org/wiki/3_GB_barrier](http://en.wikipedia.org/wiki/3_GB_barrier)

---

### Post by kosme15 on 2012-03-18
Both the CPU and the kernel are capable of addressing more than 4GB memory (in fact the 32bit PAE kernel can do it too, it's only the 32bit non-PAE kernel that has this limitation).  So the issue must be with the motherboard.  I suggest checking if there is a bios upgrade that fixes this problem.

---

