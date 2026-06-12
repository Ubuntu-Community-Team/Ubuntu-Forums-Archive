---
title: "can't adjust tty framebuffer to larger size"
date: 2007-12-15
forum: Hardware &amp; Laptops
---

### Post by jbulcher on 2007-12-15
Hello Ubuntu forums!

I'm having a spot of trouble adjusting the tty framebuffer to the value I want, which is preferably 1920x1200, but I might be happy if I figured out how to display it at 1600x1200. Funny thing is, I think I have gotten it to display at 2048x1536, because when I booted with the setting vga=0x0352, the monitor said it was outside of its range. All the other values above the default that I've tried have given me either a blank screen or many pretty colors. I'd be happy with the colors, only I'd kind of need a functional tty.

Here's what hwinfo tells me about my framebuffer:

```
root@ubuntu:/# hwinfo --framebuffer
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.447]
  Unique ID: rdCR.xJo0qtMPBs8
  Hardware Class: framebuffer
  Model: "NVIDIA NV34 Board - p162-11n"
  Vendor: "NVIDIA Corporation"
  Device: "NV34 Board - p162-11n"
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 256 MB
  Memory Range: 0xe0000000-0xefffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

Any suggestions? I'm no longer a newbie at the linux command line, which is nice, but I'm not sure I'd claim to be 'intermediate' yet. Any help is appreciated :)

---

