---
title: "Seek New Mobo but RAID - real or fake?"
date: 2008-08-04
forum: Hardware
---

### Post by celem on 2008-08-04
I am putting together a new ATX-tower size PC. After years of dual booting, I want to switch to pure Linux and run Windows only as WINE or virtualization.

I want to use three SATA drives setup with one SATA drive as the OS drive and two more SATA drives as a RAID-1 data disk. I was evaluating ASUS and Gigabyte options of both Socket 775 and AM2 and then I hit a snag concerning RAID and Linux. When I was reading the manual for a Mobo (not ASUS or Gigabyte), the RAID setup stated in bold letters "**For XP and Vista only**". I realized that some on-boards, maybe all, are partially software driven, much like the WinModems. I have read that ASUS mobos are fake-Raid so this got me a bit worried about raid compatibility with Linux.

Can anyone recommend or provide guidance on motherboards with integral RAID-1 that work will with Linux??

---

### Post by tamoneya on 2008-08-04
unless you pay up for server hardware you arent going to get real hardware raid.  The best thing to do is to make a software raid.  That is what I have on my desktop.  It has more over head on the CPU but with the multi core speed of todays CPUs you wont even notice it.

---

### Post by hotweiss on 2008-08-05
The motherboard RAID functionality cannot be utilized in Linux, as it isn't based on a real RAID controller.

---

### Post by celem on 2008-08-05
I found an interesting 1997 post on linuxmafia.com and pasted it below. It appears that work is being done on fakeraid support. Assuming that fakeraid is not available yet, I assume that I can always enable the Linux software RAID package.
----------------
RAID issues (a separate wrinkle): (link)

Most ATA RAID host adapters (except 3Ware Escalade, Adaptec 24x0, Areca, HP/Compaq, IBM ServeRAID, Intel SRC*/ICP Vortex, LSI Logic MegaRAID 150-4/150-6, and Tekram) turn out, upon examination, to not be real hardware RAID, but rather software/BIOS-dependent fakeraid. (I.e., missing hardware functionality is traditionally emulated inside idiosyncratic, undocumented, and proprietary software drivers, to hit low price points). Fakeraid is difficult to support in Linux — absent either reverse-engineering, special proprietary drivers, or (rare) manufacturer cooperation. (HighPoint, LSI Logic, Nvidia, Promise, and VIA provide proprietary drivers to support their respective fakeraids. I personally would steer clear.)

Linux often cannot read existing fakeraid volumes on such host adapters, unless you're willing to use proprietary fakeraid drivers (where available). But unless you're dual-booting MS-Windows, you shouldn't care, because Linux's software RAID (kernel "md" driver) is much faster and more reliable. You're advised to blow away fakeraid volumes, use SATA drives as straight block devices, and enable Linux software RAID instead, during Linux installation.

**Kernel coders are slowly figuring out some fakeraid variants, and coding ataraid/dmraid modules**.

---

### Post by celem on 2008-08-09
Thanks!

---

