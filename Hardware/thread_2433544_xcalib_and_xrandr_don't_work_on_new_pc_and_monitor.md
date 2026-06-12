---
title: "xcalib and xrandr don't work on new pc and monitor"
date: 2019-12-20
forum: Hardware
---

### Post by rattskjelke on 2019-12-20
I got a new pc and monitor and installed Xubuntu 19.10 on it.
On my old laptop I could use xcalib or xrandr to adjust the display gamma and contrast.

I discovered on the new pc/monitor that xcalib and xrandr don't appear to do anything.
This is the first time I have used a machine with UEFI with a monitor using HDMI. Also I have to boot with "nomodeset" in the grub config or I get a blank green screen. I don't know if any of that affects xcalib or xrandr.
Xrandr says the display name is "default". Is that right?
```

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1920 x 1080, current 1920 x 1080, maximum 1920 x 1080
default connected 1920x1080+0+0 0mm x 0mm
   1920x1080     77.00*

```
I tried changing things with "--output default" but nothing happens.
If I use xcalib nothing happens either.
I would appreciate troublelshooting suggestions.

Here is the hardware
```

CPU:       Topology: Quad Core model: AMD Ryzen 5 3400G with Radeon Vega Graphics bits: 64 type: MT MCP 
           L2 cache: 2048 KiB 
           Speed: 1260 MHz min/max: 1400/3700 MHz Core speeds (MHz): 1: 1259 2: 1369 3: 1256 4: 1257 5: 1296 6: 1386 
           7: 1311 8: 1339 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Picasso driver: N/A 
           Display: server: X.Org 1.20.5 driver: ati,fbdev unloaded: modesetting,radeon,vesa 
           resolution: 1920x1080~77Hz

```

---

### Post by mörgæs on 2019-12-22
This hardware is so new that 19.10 might not even be suitable. 

Does a live boot of 20.04 behave differently?

---

### Post by rattskjelke on 2019-12-22
> **mörgæs said:**
> This hardware is so new that 19.10 might not even be suitable. 

Does a live boot of 20.04 behave differently?

Xubuntu 20.04 does the same thing. It boots to a green screen unless I use nomodeset and select legacy boot instead of EFI boot in the BIOS settings before grub starts.

Xubuntu 18.04.3 and Linux Mint 19.3 both boot to the dekstop in EFI mode without touching anything. I didn't do any upgrades. I installed xcalib and it works on both of those.

I don't have a clue how to troubleshoot this. I did notice on 19.10 if I disabled quiet and splash I got an error in the console that said something like *ERROR: VGACON disables amdgpu kernel modesetting*. I forgot now if that was with nomodeset or not.

---

### Post by rattskjelke on 2019-12-22
Here is some system info reported by inxi for all three...
```

Xubuntu 19.10
Kernel: 5.3.0-24-generic x86_64 bits: 64 compiler: gcc v: 9.2.1 Desktop: Xfce 4.14.1
Graphics:
Device-1: AMD Picasso
vendor: Hewlett-Packard
driver: N/A
bus ID: 07:00.0 
chip ID: 1002:15d8 
Display: x11
server: X.Org 1.20.5
driver: ati,vesa 
unloaded: fbdev,modesetting,radeon
resolution: 1920x1080~N/A 
OpenGL: renderer: llvmpipe (LLVM 9.0 128 bits)
v: 3.3 Mesa 19.2.1
compat-v: 3.1 
direct render: Yes

Xubuntu 18.04.3
Kernel: 5.0.0-23-generic x86_64 bits: 64 gcc: 7.4.0 Desktop: Xfce 4.12.3 (Gtk 2.24.31)
Graphics:
Card: Advanced Micro Devices [AMD/ATI] Picasso
bus-ID: 07:00.0
chip-ID: 1002:15d8
Display Server: x11 (X.Org 1.20.4 )
drivers: ati,amdgpu
(unloaded: modesetting,fbdev,vesa)
Resolution: 1920x1080@60.00hz
OpenGL: renderer: AMD RAVEN (DRM 3.27.0, 5.0.0-23-generic, LLVM 8.0.0)
version: 4.5 Mesa 19.0.2
Direct Render: Yes

Linux Mint 19.3
Kernel: 5.0.0-32-generic x86_64 bits: 64 compiler: gcc v: 7.4.0 Desktop: Xfce 4.14.1
Graphics:  
Device-1: Advanced Micro Devices [AMD/ATI] Picasso
vendor: Hewlett-Packard
driver: amdgpu
v: kernel 
bus ID: 07:00.0
chip ID: 1002:15d8 
Display: x11
server: X.Org 1.20.4
driver: amdgpu,ati
unloaded: fbdev,modesetting,vesa 
resolution: 1920x1080~60Hz 
OpenGL: renderer: AMD RAVEN (DRM 3.27.0 5.0.0-32-generic LLVM 8.0.0)
v: 4.5 Mesa 19.0.8
direct render: Yes 


```

---

### Post by rattskjelke on 2019-12-23
I fixed it. It was the damned xfce compositor.
I found that on the Xubuntu 19.10 live USB if I turn off the montitor, Ctrl-Alt-F2 to a terminal, turn the monitor back on, then I had a display again.
I then I went back to the desktop with Ctrl-Alt-F7 and I still had a display but with lots of artifacts & junk on text and window edges.
I turned off compositing and everything worked normally.

I did the same thing on my hard drive installation of Xubuntu 19.10 and it worked too so I took nomodeset out of grub and updated grub and so far it still works.

---

