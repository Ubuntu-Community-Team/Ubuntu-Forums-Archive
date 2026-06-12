---
title: "Text Console Resolution Too Large"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by mchip22 on 2009-03-16
I have just installed Ubuntu 8.10 on a DELL Dimension XPS R400.  No Desktop environment configured, console only.

Monitor is old CRT, and upon boot text size is way too big to view the entire screen.  Something like 800x600.  

I have searched all over and tried several fixes recomended in other posts - such as editing the /boot/grub/menu.lst file, adding vga=xxx to the defoptions line at the end.  

I then ran update-grub and verified the kernel entry at the bottom of the file was indeed updated.

Then I issue shutdown -r now, and reboot.

One of two things happens - 
 1.  Either the resolution does not change
or
 2.  The display goes screwy and display green flashing boxes (think original Nintendo)

I have tried vga=791, 788, 0x311, etc.

I am able to login and fine through Putty Connection and display is fine, but I would like to fix the resolution on the server itself.

Any ideas?

Here is some information which may be useful:

ubuntu 01:00.0 VGA compatible controller: NVidia / SGS Thomson (Joint Venture) Riva128 (rev 21)

root@pcamesh:/boot/grub# hwinfo --framebuffer
02: None 00.0: 11001 VESA Framebuffer
  [Created at bios.450]
  Unique ID: rdCR.1mhJOR5jf57
  Hardware Class: framebuffer
  Model: "STB Velocity 128"
  Vendor: "STB Systems, Inc."
  Device: "Velocity 128"
  SubVendor: "STB Velocity 128 (NV3T)"
  SubDevice:
  Revision: "210-0276-003"
  Memory Size: 8 MB
  Memory Range: 0xfc000000-0xfc7fffff (rw)
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
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x0337: 400x300 (+400), 8 bits
  Mode 0x0338: 400x300 (+800), 16 bits
  Mode 0x0339: 400x300 (+1600), 24 bits
  Mode 0x033a: 512x384 (+512), 8 bits
  Mode 0x033b: 512x384 (+1024), 16 bits
  Mode 0x033c: 512x384 (+2048), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0341: 1152x864 (+1152), 8 bits
  Mode 0x0342: 1152x864 (+2304), 16 bits
  Mode 0x0343: 1152x864 (+4608), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1600x1024 (+1600), 8 bits
  Mode 0x0348: 1600x1024 (+3200), 16 bits
  Mode 0x0349: 1920x1080 (+1920), 8 bits
  Mode 0x034a: 1920x1080 (+3840), 16 bits
  Mode 0x034b: 720x480 (+1440), 16 bits
  Mode 0x034c: 720x576 (+1440), 16 bits
  Mode 0x0356: 1600x1200 (+6400), 24 bits
  Mode 0x0363: 1920x1200 (+1920), 8 bits
  Mode 0x0364: 1920x1200 (+3840), 16 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown


root@pcamesh:/boot/grub# hwinfo --monitor
20: None 00.0: 10000 Monitor
  [Created at monitor.95]
  Unique ID: rdCR.5XgUKJpwtrB
  Hardware Class: monitor
  Model: "DELL D1028L"
  Vendor: DEL "DELL"
  Device: eisa 0x730b "D1028L"
  Serial ID: "84779dKMD388"
  Resolution: 720x400@70Hz
  Resolution: 640x480@60Hz
  Resolution: 640x480@75Hz
  Resolution: 800x600@60Hz
  Resolution: 800x600@75Hz
  Resolution: 1024x768@60Hz
  Resolution: 1024x768@75Hz
  Resolution: 1024x768@85Hz
  Resolution: 800x600@85Hz
  Resolution: 1280x1024@60Hz
  Resolution: 640x480@85Hz
  Resolution: 720x350@60Hz
  Size: 250x184 mm
  Detailed Timings #0:
     Resolution: 720x350
     Horizontal:  720  738  846  900 (+18 +126 +180) -hsync
       Vertical:  350  388  390  449 (+38 +40 +99) +vsync
    Frequencies: 28.32 MHz, 31.47 kHz, 70.08 Hz
  Driver Info #0:
    Vert. Sync Range: 50-120 Hz
    Hor. Sync Range: 31-70 kHz
  Config Status: cfg=new, avail=yes, need=no, active=unknown

21: None 00.1: 10000 Monitor
  [Created at monitor.95]
  Unique ID: jyhG.5XgUKJpwtrB
  Hardware Class: monitor
  Model: "DELL D1028L"
  Vendor: DEL "DELL"
  Device: eisa 0x730b "D1028L"
  Serial ID: "84779dKMD388"
  Resolution: 720x400@70Hz
  Resolution: 640x480@60Hz
  Resolution: 640x480@75Hz
  Resolution: 800x600@60Hz
  Resolution: 800x600@75Hz
  Resolution: 1024x768@60Hz
  Resolution: 1024x768@75Hz
  Resolution: 1024x768@85Hz
  Resolution: 800x600@85Hz
  Resolution: 1280x1024@60Hz
  Resolution: 640x480@85Hz
  Resolution: 720x350@60Hz
  Size: 250x184 mm
  Detailed Timings #0:
     Resolution: 720x350
     Horizontal:  720  738  846  900 (+18 +126 +180) -hsync
       Vertical:  350  388  390  449 (+38 +40 +99) +vsync
    Frequencies: 28.32 MHz, 31.47 kHz, 70.08 Hz
  Driver Info #0:
    Vert. Sync Range: 50-120 Hz
    Hor. Sync Range: 31-70 kHz
  Config Status: cfg=new, avail=yes, need=no, active=unknown

---

### Post by mchip22 on 2009-03-25
Any help on this would be appreciated.  Could it simply be graphics card issue?

---

### Post by Yashiro on 2009-03-26
try adding vga=ask

Also there is no need to run update-grub when you only make this change.

---

