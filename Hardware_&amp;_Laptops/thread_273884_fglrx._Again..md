---
title: "fglrx. Again."
date: 2006-10-08
forum: Hardware &amp; Laptops
---

### Post by simon360 on 2006-10-08
I decided to give fglrx another whirl today, and I got somewhere, but I'm stuck now. I've always had this problem, but the ATI Mobility Radeon 9000 is officially supported by the fglrx driver; I don't know why it doesn't work.

Anyway, I figured out that fglrx was not being loaded at startup, so I did "sudo modprobe fglrx", which got it started. dmesg | grep fglrx now looked like this:
```

simon@simon-laptop:~$ dmesg | grep fglrx
[17180688.964000] [fglrx] Maximum main memory to use for locked dma buffers: 372 MBytes.
[17180688.964000] [fglrx] module loaded - fglrx 8.29.6 [Sep 19 2006] on minor 0
simon@simon-laptop:~$        

```
I thought I had it figured out, but then I restarted X, and dmesg | grep fglrx looked more like this:

```
simon@simon-laptop:~$ dmesg | grep fglrx
[17180688.964000] [fglrx] Maximum main memory to use for locked dma buffers: 372 MBytes.
[17180688.964000] [fglrx] module loaded - fglrx 8.29.6 [Sep 19 2006] on minor 0
[17180706.112000] [fglrx:firegl_init_mask_ram] *ERROR* maskram_type not detected
[17180706.112000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17180706.112000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17180706.112000] [fglrx] AGP detected, AgpState   = 0x1f00021b (hardware caps of chipset)
[17180706.112000] [fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
[17180706.112000] [fglrx] total      GART = 33554432
[17180706.112000] [fglrx] free       GART = 17559552
[17180706.112000] [fglrx] max single GART = 17559552
[17180706.112000] [fglrx] total      LFB  = 60911616
[17180706.112000] [fglrx] free       LFB  = 48623616
[17180706.112000] [fglrx] max single LFB  = 48623616
[17180706.112000] [fglrx] total      Inv  = 0
[17180706.112000] [fglrx] free       Inv  = 0
[17180706.112000] [fglrx] max single Inv  = 0
[17180706.112000] [fglrx] total      TIM  = 0
simon@simon-laptop:~$  
```      

And fglrxinfo still looked like this:

```
simon@simon-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

simon@simon-laptop:~$    
```

I'm at a complete loss, and would really appreciate any help with this. I'd also like to know why fglrx isn't being modprobed on startup, and if that's affecting this.

I compiled this based on the driver provided from ATI, not from the official apt-get sources, since they weren't working for me.

---

### Post by David Corrales on 2006-10-09
Did you blacklist the repo drivers? If not, those are loading up, and not the ones you manually installed.

---

### Post by fishwithapipe on 2006-10-09
Ah nice and simple this one.

The radeon 9000 is NOT supported by the 8.29.6 driver.

The previous 8.28 driver IS.

Goodluck

---

### Post by simon360 on 2006-10-09
Ok, it's blacklisted. And IIRC, the Radeon 9000 is not supported, but the 9000 **Mobility** is.

---

### Post by fishwithapipe on 2006-10-09
er, no it isnt

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

> ATI Proprietary Linux x86 Display Driver

As of driver version 8.29.6 support for the following products is no longer included:

    * Radeon® 8500/9000/9100/9200/9250
    * Mobility™ Radeon® 9000/9100/9200
    * Radeon® IGP 9000/9100/9200

Users with these products should use driver version 8.28.8

---

### Post by simon360 on 2006-10-09
Huh, interesting...

I'll go look into that

---

