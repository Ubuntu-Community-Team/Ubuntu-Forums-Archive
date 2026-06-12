---
title: "AMD dual-graphics not detected"
date: 2015-06-14
forum: Hardware
---

### Post by Inoki on 2015-06-14
I own a Lenovo G50-45 laptop (full AMD with **A6-6310 APU**) which comes with **AMD Radeon R4** and **R5** graphic cards. Problem is even though I have a fully up-to-date 14.04.2 x64 with the latest catalyst 15.101.1001 installed only the R4 graphic card (the weaker one) is detected.

What can be done to get the most of my system again?

GFX info via *hardinfo*:

```
-Display-
Resolution        : 1366x768 pixels
Vendor        : The X.Org Foundation
Version        : 1.16.0
-Monitors-
Monitor 0        : 1366x768 pixels
-Extensions-
AMDXVBA
AMDXVOPL
ATIFGLEXTENSION
ATIFGLRXDRI
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
DRI3
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
Present
RANDR
RECORD
RENDER
SECURITY
SGI-GLX
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-VidModeExtension
XINERAMA
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
glesx
-OpenGL-
Vendor        : Advanced Micro Devices, Inc.
Renderer        : AMD Radeon(TM) R4 Graphics 
Version        : 4.4.13372 Compatibility Profile Context 15.101.1001
Direct Rendering        : Yes


```
Before I had Windows 8.1 on this laptop and everything ran smooth, I was able to select cards. BIOS also allow for graphics switching.

---

### Post by Inoki on 2015-06-14
Upgrading to 15.04 might solve this, as doing a brief check via LiveUSB I saw that both cards are detected. Although there are still issues with e.g. Libreoffice crashing the entire sessino I might give it a shot and give WPS Office a shot. Closing.

---

