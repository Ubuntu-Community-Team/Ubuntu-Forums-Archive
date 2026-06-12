---
title: "Boot very slow and no splash screen + gnome slow"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by hbutu on 2008-02-03
Hi, I have Ubuntu 7.10 x86_64 on a VAIO VGN-NR21S/S. After grub boot message my laptop screen shuts down for a while (1min30) until gnome login screen appears and then gnome starts very very slowly (about 2min).

```

~$ uname -a
Linux horia-laptop 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 x86_64 GNU/Linux

~$ dmesg | grep ailed
[   19.106155] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:01:00.0
[   23.047320] PM: Resume from disk failed.

~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GT (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

And my bootcharts with usplash on and without:

---

### Post by stalker145 on 2008-02-04
> **hbutu said:**
> Hi, I have Ubuntu 7.10 x86_64 on a VAIO VGN-NR21S/S. After grub boot message my laptop screen shuts down for a while (1min30) until gnome login screen appears and then gnome starts very very slowly (about 2min).

This sounds like the same problem I had when I installed 7.10 on my Dell. Try this out and see if it works:```
sudo nano /boot/grub/menu.lst
```Find your primary boot which probably looks like this:```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic boot=UUID=5a9e8f79-40ed-4897-a16e-3d8b4b21d3d7 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```and delete the word "splash" from the kernel line. Reboot your computer and all should be well in the world.

---

### Post by midnightray on 2008-02-04
Try disabling the service "cupsd" worked for my friend:

System -> Administration -> Services. Untick "Printer service (cupsys)" and see if this helps.

---

### Post by hbutu on 2008-02-04
Neither of above trick seems to work :(

---

### Post by hbutu on 2008-02-06
I replaced my gutsy amd64 with the i386 gutsy and all problems seems to solve now :) .
Seems to be a amd64 issue. My CPU is a Intel T5450 it should work ?

---

### Post by envygeeks on 2008-02-14
This isn't an AMD64 issue, this is a Gutsy issue.  Unless that's what you mean.  You aren't the first to have trouble with any sort of anything on Gutsy and it's current Kernel.  I hope they get on the ball and address the x64 issues so we can get to using the real power of x64 eventually =P.  This issue with sluggishness and bad graphics have been reported on Intels too I believe.

---

### Post by sunyata on 2008-02-16
> **stalker145 said:**
> This sounds like the same problem I had when I installed 7.10 on my Dell. Try this out and see if it works:```
sudo nano /boot/grub/menu.lst
```Find your primary boot which probably looks like this:```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic boot=UUID=5a9e8f79-40ed-4897-a16e-3d8b4b21d3d7 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```and delete the word "splash" from the kernel line. Reboot your computer and all should be well in the world.

Hi,
I tried deleting "splash" in the Grub -file as described on my mothers DELL (she is 80!). It seemed to help.
I will try it on mine too.

Thanks

Sunyata

---

### Post by trieb on 2008-02-16
I have an ibm t42 that did not show the boot screen, and removing the splash argument in the grub menu list enabled the cmd line messages during boot.  Ill post back if I find anything about fixing it, as its our job not "they" to figure out how to figure it out.

---

