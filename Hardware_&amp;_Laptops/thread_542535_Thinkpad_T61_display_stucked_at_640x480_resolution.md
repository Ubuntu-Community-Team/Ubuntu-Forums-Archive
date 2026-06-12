---
title: "Thinkpad T61 display stucked at 640x480 resolution"
date: 2007-09-04
forum: Hardware &amp; Laptops
---

### Post by Kxpress on 2007-09-04
I just installed the Nvidia Driver for my Thinkpad T61 Laptop, 15.7' WSGA+ Screen with Quadros NVS 140M, 128 MB (but on Nvidia setting window shows VBIOS Version 60.86.3e.00.00; Memory 512 MB; Bus type: PCI Express 16X).

My screen now displayed at 640x480 resolution, looks awkward...

On the NVIDIA X Server Settings Window:

X Server Information:
Operating sSystem Linux-x86_64
NVIDIA Driver Version: 100.14.11
Server Version: X11
Server Vendor String: The X.Org Foundation.
Server Vendor Version: 7.2.0 (70200000)

X Server Display Configuration show a screen with words: "IBM 640 x 480"

Go down to DFP-0 (IBM)

Native Resulution 1680x1050
Best Fit Resolution 1680x1050
Front End Resolution 640x480
Back End Resolution 1680x1050
Refresh Rate 59.98 MHz

I selected "Force Full GPU Scalling"
GPU Scalling method:
- select stretched or Aspect Ratio : the screen looks awkward with big fonts, big icons/windows
- select "Centered" : whole screen shrunk to a small display area, ofcourse the display's quality is very good for the small area.
I already tried to reconfigure by use the command line:
"sudo dpkg-recongifure xserver-xorg"
tried to force this resolution but no thing changed

What do I need to do to make it usable i.e. full screen of 1680x1050 pixels  as in the Windows environment ?

---

