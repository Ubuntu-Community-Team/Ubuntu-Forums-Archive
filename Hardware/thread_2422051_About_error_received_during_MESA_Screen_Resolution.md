---
title: "About error received during MESA Screen Resolution change"
date: 2019-07-01
forum: Hardware
---

### Post by lsuersoy on 2019-07-01
Hello there,

HP Pavilion DV7 2012 Ubuntu MATE 19.04 64 Bit is installed in the factory notebook.
No-use UEFI Bios.
The only next next setup failed.
I had to set it up with NOMODESET.
 
Computer and OS features are as follows.
```
Computer- Processor        : Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
Memory            : 8111MB (1613MB used)
Machine Type            : Notebook
Operating System        : Ubuntu 19.04
 
 
-Display- Resolution        : 1024x768 pixels
OpenGL Renderer        : llvmpipe (LLVM 8.0, 256 bits)
X11 Vendor            : The X.Org Foundation
 
 
-Display- Resolution        : 1024x768 pixels
Vendor                 : The X.Org Foundation
Version            : 1.20.4
Current Display Name    : :0
-Monitors- Monitor 0        : 1024x768 pixels
-OpenGL- Vendor        : VMware, Inc.
Renderer            : llvmpipe (LLVM 8.0, 256 bits)
Version            : 3.1 Mesa 19.0.2
Direct Rendering        : Yes
```
 1 - The following code shows my Internal and External video cards.
 ```
lspci -nnk | grep -iA2 vga
```
1 - Command Result:
```
 00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)

     Subsystem: Hewlett-Packard Company 2nd Generation Core Processor Family Integrated Graphics Controller [103c:3389]

     Kernel modules: i915

 --
 01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6730M/6770M/7690M XT] [1002:6740]

     Subsystem: Hewlett-Packard Company Radeon HD 6770M [103c:3389]

     Kernel modules: radeon


``` 
 
 I wanted the information for resolution with the following command.
 ```
cvt 1280 1024
```  Command Result::  
 ```
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz

  Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync


```  
I wanted to set the new display mode. The name will be "new";
```
xrandr --newmode "new" 109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```

But; I got the following error. What is the reason of this ? How can we get over it?
```
 xrandr: Failed to get size of gamma for output default


```  
 What can we do to adjust the resolution?

---

### Post by lsuersoy on 2019-07-02
I was surprised. I asked a question 13 hours ago. 200,000 people were on-line. And not one person answered. This platform no longer means anything to me. Enjoy yourself.

---

### Post by lsuersoy on 2019-07-02
I didn't make sense of 10 postings.

---

