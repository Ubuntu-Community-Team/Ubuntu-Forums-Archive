---
title: "Wacom Intuos S Bluetooth not working"
date: 2018-05-14
forum: Hardware
---

### Post by betazoid26 on 2018-05-14
Hi, I have Ubuntu 16.04 and a Wacom Intuos S Bluetooth (newest model). The problem is: the tablet works just fine if it is connected with a USB cable, but it does not if it is connected via bluetooth. It does show up as a (connected) bluetooth device in the system but it does not do anything. Apparently it is not recognized as a specific device.
Thanks in advance for the help
Anna

---

### Post by mörgæs on 2018-05-14
Does 18.04 work better?

---

### Post by betazoid26 on 2018-05-14
I have not installed 18.04 yet, only tested it on a pendrive. In the live-system the device does not work when connected via bluetooth.

---

### Post by mörgæs on 2018-05-15
A live boot is fine for testing. 
Do other Bluetooth devices work?

---

### Post by betazoid26 on 2018-05-16
Yes, they work just fine
Apparently, the tablet works when connected via usb, but it is not recognized as a tablet. It does not show up in the budgie system settings under Wacom tablet
However, in Krita pressure sensitivity works fine. When connected via usb. No functionality when connected via bluetooth

---

### Post by mörgæs on 2018-05-18
I think that for now best is to use the tablet with wire. 

Wacom is generally known to be a GNU/Linux-friendly company so there is a chance that the necessary drivers will soon be added. The S model is new which could explain that the software is lacking a little.

---

### Post by betazoid26 on 2018-05-19
Well, the problem is partly solved. It's secure boot which is causing it.
Here is what I did:

1. compled and installed the newest wacom driver on a persistent live system on a pendrive
2. result: the tablet did not work at all, not even with usb
3. I googled and switched off secure boot
4. everything perfect, device works with bluetooth but
5. I cannot boot my regularly installed system without secure boot. I had to configure secure boot so it could boot the system. I can only boot live systems on pendrives without secure boot

I googled a bit and I found out that it is possible to sign custom kernel modules so they are not blocked by secure boot. But it is way above my linux-level.

So I guess, for now, I am stuck with the wire.

---

### Post by mörgæs on 2018-05-20
There is hardly an end to the nuisance caused by 'secure' boot. Free-as-in-speach is essentially a thing of the past, as this example demonstrates.

Since the source code works in a live boot it will likely be default in Ubuntu 18.10. Until then Windows users are favoured. 

> **betazoid26 said:**
> 
5. I cannot boot my regularly installed system without secure boot.


Which system? I believe that even Windows 10 allows a non-restricted boot.

---

### Post by betazoid26 on 2018-05-21
Yes, Windows does allow booting without secure boot, but Ubuntu does not, at least a regular installation, most live linux systems to allow booting without secure boot. It depends on how the live system was created.
Either it is a dual-boot-thing, or my laptop would not even allow to boot linux without secure boot if it were the only OS.

I have had both Linux and Windows for many years and I was happy that way. 2 years ago I bought a new laptop. And I was forced to use Windows only, because of the secure boot thing. A few weeks ago I googled and found out how it is possible to confugure secure boot so it does boot linux.
Secure boot/UEFI has one advantage though: On my previous laptop, when I installed linux on the hd, the original boot manager was overwritten and I could not access my Windows-recovery-partition any more. That is not an issue with UEFI any more.

---

### Post by mörgæs on 2018-05-22
> **betazoid26 said:**
> Windows does allow booting without secure boot, but Ubuntu does not, at least a regular installation

Then there is something wrong with the installation. Ubuntu does certainly not require 'secure' boot enabled. 

I can't troubleshoot that, though.

---

### Post by betazoid26 on 2018-05-23
Well, I tried to install the bootloader to the efi-partition of my pendrive, nevertheless ubuntu put it - at least some efi-files which are necessary for booting - to the efi-partition of my internal ssd (sda). But I am sure there is nothing wrong with the installation. I read that dual booting is the same on all newer Acer laptops. It is necessary to configure secure boot.

---

### Post by oldfred on 2018-05-25
Acer's require you to set an UEFI password which requires UEFI secure boot on. And then you have to enable "trust" for the Ubuntu/grub .efi boot files in the ESP - efi system partition from within UEFI.
Most systems do not need the UEFI password to be set. And you must always remember it, or clear it after use, or you can make getting into UEFI difficult or impossible.

Ubuntu will install with Secure Boot on or off. 
But to install any proprietary drivers you must have Secure Boot off. Ubuntu cannot certify that a proprietary driver is "Secure" or in the security boot chain. They may later find a way to do that, but for now if you need proprietary drivers keep UEFI Secure Boot off.

It seems almost every brand of system has some sort of unique requirement. And some of the larger brands, different models may need different settings or boot methods. It would be nice if they actually followed the UEFI "standard".

---

