---
title: "Server install &amp; SATA"
date: 2006-10-24
forum: Hardware &amp; Laptops
---

### Post by Tankard on 2006-10-24
I have server installed on a PATA drive and was hoping to use my SATA drive as storage. I can't see the sata drive in fdisk or by any other method. After scouring the net for support and then, these forums, I haven't found exactly what I am looking for. I see support threads for RAID, but not for setting up SATA recognition in server.

I have Ubuntu desktop installed on another machine, and it mounts a SATA drive used by my Windows partition...

Thanks for any help.

More info;

I have a VIA VT6420 SATA controller which is recognized when I run the lspci command.

So this tells me I have the controller drivers loaded, but still can't find the drive.

---

### Post by kidders on 2006-10-24
Hi there,

What does your dmesg say about your SATA disks? If your server can talk to USB storage devices, chances are it can do serial hard drives too :-) Did you tinker with your kernel at all, by any chance?

---

### Post by Tankard on 2006-10-24
I don't tinker with the kernel.

There are no USB devices actually hooked up to the MB, unless you count the onboard connection to the front of the case.

I am not quite sure what you mean by "dmesg".

---

### Post by bay-bee on 2006-10-24
Open a terminal and run a program called "dmesg" it will give you information from the kernel as it booted your machine (will give you information about SATA disks etc)

---

### Post by kidders on 2006-10-25
Sorry, I should've been a little clearer about that :-? The messages can be tough to decypher if you're not used to it. If you like, pm me yours and I'll take a quick look ... although it *should* be okay to post it if you prefer.

---

