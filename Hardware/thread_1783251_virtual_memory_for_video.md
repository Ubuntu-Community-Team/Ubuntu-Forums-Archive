---
title: "virtual memory for video"
date: 2011-06-15
forum: Hardware
---

### Post by Bencze on 2011-06-15
Hi!

Is there any way to allocate virtual memory for my videocard in ubuntu 10.04. Because I've an IBM X41 laptop with a 128Mb graphic card and it seems to me a bit weak. Thanks in advanced!

Sinya

---

### Post by wolfen69 on 2011-06-15
Swap is the equivalent of virtual memory. Check in system monitor for how much you have.

---

### Post by Yellow Pasque on 2011-06-15
I think you're barking up the wrong tree. The Intel GMA900 is weak in general. Allocating more RAM for it probably isn't going to do anything on apps that this GPU can actually run..
You should double check that 3D accel is working properly:
```
glxinfo
```

---

### Post by DanneStrat on 2011-06-15
> **Bencze said:**
> Hi!

Is there any way to allocate virtual memory for my videocard in ubuntu 10.04. Because I've an IBM X41 laptop with a 128Mb graphic card and it seems to me a bit weak. Thanks in advanced!

Sinya

Hi.

Have you tried to go into bios setup and see if you can find the option there?

First reboot, then press the appropriate key to enter setup. The option you want to change is often referred to as UMA. On my hp pavilion, I enter setup and in the video settings, I select to use "UMA+sideport" and specify the amount of ram I want to dedicate to my graphics card. See if you can find a similar setting in your setup.

UMA=the setting that let you give some of your RAM to the graphics card

Sideport memory=the dedicated video memory(in your case 128 MB)

---

### Post by Yellow Pasque on 2011-06-15
> **DanneStrat said:**
> Hi.

Have you tried to go into bios setup and see if you can find the option there?

First reboot, then press the appropriate key to enter setup. The option you want to change is often referred to as UMA. On my hp pavilion, I enter setup and in the video settings, I select to use "UMA+sideport" and specify the amount of ram I want to dedicate to my graphics card. See if you can find a similar setting in your setup.

UMA=the setting that let you give some of your RAM to the graphics card

Sideport memory=the dedicated video memory(in your case 128 MB)
This model uses basic Intel video. It doesn't have sideport memory dedicated to the video card. Also, allocating more system memory probably won't help and will only decrease the amount of system RAM available (which may be very noticeable if only 512MB of RAM).

---

