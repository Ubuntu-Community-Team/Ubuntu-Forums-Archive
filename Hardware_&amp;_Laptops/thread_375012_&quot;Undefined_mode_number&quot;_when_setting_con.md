---
title: "&quot;Undefined mode number&quot; when setting console font"
date: 2007-03-03
forum: Hardware &amp; Laptops
---

### Post by cvk on 2007-03-03
I installed Edgy a while ago and everything works fine, but I always get that annoying warning message immediately after selecting the boot entry in GRUB: "You passed an undefined mode number".

I'm using the standard generic Ubuntu kernel (Linux 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux) and I have set the mode number according to the output of hwinfo:

```
# hwinfo --framebuffer
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.440]
  Unique ID: rdCR.2nOy6PHVBI2
  Hardware Class: framebuffer
  Model: "NVIDIA nv43 Board - p218h2  "
  Vendor: "NVIDIA Corporation"
  Device: "nv43 Board - p218h2  "
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 128 MB
  Memory Range: 0xd0000000-0xd7ffffff (rw)
  ...
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  ...
  Config Status: cfg=new, avail=yes, need=no, active=unknown

# grep ^kernel /boot/grub/menu.lst
kernel          /vmlinuz-2.6.17-10-generic root=/dev/hda3 ro vga=0x31b


```

Neither using the hex value (0x31b) nor the decimal value (795) did work.

---

