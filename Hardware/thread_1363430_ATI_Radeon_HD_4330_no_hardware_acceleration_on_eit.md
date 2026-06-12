---
title: "ATI Radeon HD 4330: no hardware acceleration on either driver?"
date: 2009-12-24
forum: Hardware
---

### Post by DaVince21 on 2009-12-24
Hi,

I have a new laptop, bought with consideration to how compatible its hardware will be with Ubuntu. However, it turns out that I can NOT get proper 3D hardware acceleration working with the video card (chipset?) that's in it.

The video card in question is the ATI Radeon HD 4330.

According to the documentation of both the open-source driver and the fglrx driver, it's supposed to be supported. Or at least, one would expect it to be if the "HD 4300 series" and "Radeon 4350" are both mentioned in those documents. Though the 4330 is not mentioned specifically, one would expect the 4300 driver to pick up on it anyway, especially since [this page on the Ubuntu wiki](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) specifically mentions this example:
>  the ATI Radeon 4670 graphics card is covered under the section ATI Desktop Product Family Support with the specific pointer ATI Radeon™ HD 4600 Series.

So, I'm stumped. The open-source driver leaves me with 2D acceleration only, which is not enough for the OpenGL games I occasionally play, and the fglrx driver doesn't give me OpenGL acceleration *at all*, giving me errors such as this one when I try to run the control center:

```
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    135 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x17
amdcccle: ../../src/xcb_io.c:542: _XRead: Assertion `dpy->xcb->reply_data != ((void *)0)' failed.
Aborted
```

Some more details:
**lshw -c video**
```
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: M92 LP [Mobility Radeon HD 4300 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
       resources: memory:e0000000-efffffff(prefetchable) ioport:7000(size=256) memory:f2100000-f210ffff memory:f2120000-f213ffff(prefetchable)
```

I am currently using the latest fglrx driver downloaded from ati.com (though it doesn't work, at least X still starts). (Edit: reverted back to the open-source driver for now.)

I am running a 32-bit version of Ubuntu on my Intel 64-bit dual-core system.

Edit: perhaps it's important to mention I'm running kernel 2.6.32 from [http://kernel.ubuntu.com/~kernel-ppa/](http://kernel.ubuntu.com/~kernel-ppa/) because otherwise my wireless network card won't work well.

I couldn't find a related thread to my specific card, hence this topic. Any help will be greatly appreciated.

---

### Post by dnyal on 2010-01-30
Apparently, this guy got it working using a new driver from ATI site: [http://ubuntuforums.org/archive/index.php/t-1239813.html](http://ubuntuforums.org/archive/index.php/t-1239813.html)

I just checked the site, and there's a new 2010 version. Follow the directions in the driver documentation, try if it works for you and feedback. Hope this helps. ;)

---

### Post by barna on 2010-05-28
Hi,
According to ATI's installation guide
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)
their Catalyst driver is now in Ubuntu Lucid (10.04) repository, so you can install it. I guess this driver will drive the HD 4330. I would be happy to hear further updates on this topic, since most probably in the coming few days I want to buy a Dell Inspiron 1564 with this graphics card.

There is a commend on ATI's site [http://support.amd.com/fr/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English](http://support.amd.com/fr/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English)
> 
32-Bit packages must be installed for 64-Bit Linux drivers to install or work

which I don't quite understand (32-bit packages of what? the driver?) But I guess this is taken care of in the Ubuntu repository.

Anyway, any feedback about this would be welcome.

---

### Post by clockworkpc on 2011-01-19
Am currently installing the newest driver available from the ATI website.

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

Installing version 8.8x on Xorg 7.6.

Will let you know how it goes.

---

### Post by clockworkpc on 2011-01-19
Am currently installing the newest driver available from the ATI website.

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

Installing version 8.801 on Xorg 7.6.

Will let you know how it goes.

---

### Post by clockworkpc on 2011-01-19
Installation successful.  Rebooting now...

---

### Post by clockworkpc on 2011-01-19
Nope.  The latest driver to date from ATI works terribly.  I've lost all acceleration, no compiz, no nothing.

Does anyone know how to uninstall the ATI driver if you install it via the shell script?

---

### Post by clockworkpc on 2011-01-19
Am re-installing fglrx via Synaptic.  Let's see how that goes.

---

