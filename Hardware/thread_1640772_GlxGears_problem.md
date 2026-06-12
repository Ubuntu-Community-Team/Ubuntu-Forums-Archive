---
title: "GlxGears problem"
date: 2010-12-08
forum: Hardware
---

### Post by Dsky on 2010-12-08
Hi,

i've a Toshiba M40-282, with an ati mobility x700.

I tried Fedora and Ubuntu and I'm having the same problem..

The pc is fast in anything except in flash player or running glxgears (3d?)

running glxgears the pc starts slowing down as when i watch videos in flash

what can I do? 

thanks!
Phil

ps. now I'm using Ubuntu 9.10 because i cant use 10.04 without setting the effects in the Aspect window to None (or nothing, i dont know in english), setting normal all the pc is slow.
I tried installing 10.10 but it doesn't even start... i see only a black screen after the boot...
I tried Fedora 14 too and like ubuntu 9.10 is all fast except in flash stuff

---

### Post by matt_symes on 2010-12-08
Hi

glxgears uses openGL with 3G. What driver are you using?

Kind regards

---

### Post by Dsky on 2010-12-08
```
 **lspci | grep -i vga**
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)

**dpkg -l | grep fglrx**
ii  fglrx-modaliases                     2:8.660-0ubuntu4.1                         Identifiers supported by the ATI graphics dr

** glxinfo | grep render**
direct rendering: Yes
OpenGL renderer string: Mesa DRI R300 (RV410 5653) 20090101 x86/MMX/SSE2 TCL




```

---

### Post by matt_symes on 2010-12-08
Hi

Have a look at this thread. It suggests the chip is no longer supported by ATI and so you are using the open source drivers and not the ATI drivers, hence your 3D and speed issues. The x700 is an old card.

> FGLRX does not support ATI MOBILITY Radeon X700 in Lucid.


Read these threads.

[http://ubuntuforums.org/showthread.php?t=1411584](http://ubuntuforums.org/showthread.php?t=1411584)
[http://ubuntuforums.org/showthread.php?t=1333275](http://ubuntuforums.org/showthread.php?t=1333275)
[http://wiki.ubuntuforums.org/showthread.php?t=1542673](http://wiki.ubuntuforums.org/showthread.php?t=1542673)

Kind regards

---

### Post by Dsky on 2010-12-08
exactly what does it mean?  I can't use linux on my notebook?  The notebook isn't that old....

---

### Post by matt_symes on 2010-12-08
Hi

I will have to bow out of this thread as i don't know enough about your notebook to give you a definitive answer.

I can only say that here is what i have....

```

matthew@matthew-laptop:/var/log$ dpkg -l | grep fglrx
ii  fglrx                                 2:8.723.1-0ubuntu5                              Video driver for the ATI graphics accelerato
ii  fglrx-amdcccle                        2:8.723.1-0ubuntu5                              Catalyst Control Center for the ATI graphics
ii  fglrx-modaliases                      2:8.723.1-0ubuntu5                              Identifiers supported by the ATI graphics dr
``````
matthew@matthew-laptop:~$ lspci -k | grep -iA2 vga
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
        Kernel driver in use: fglrx_pci
        Kernel modules: fglrx, radeon
```I acquired fglrx and fglrx-amdcccle after installing the ATI propitiatory drivers for my card. The ATI drivers gave me good 3D support that the open source ones did not.

Sorry i cannot give you a definitive answer. Hopefully some else will know or show you another way (and i will also learn something).

Kind regards

---

### Post by Dsky on 2010-12-08
thanks anyway...

so i wait for someone else who could help me :popcorn:

maybe i'll try installing ubuntu 8.10

---

### Post by matt_symes on 2010-12-08
Hi

Well, i have found definitive proof that your graphics card is no longer supported by ATI and cant use the fglrx driver.

From [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

> 
**Which cards do ATI no longer support?** The ATI Radeon 9500-9800, Xpress200-1250, 690G, 740G, X300-X2500  (including Mobility RadeonHD 2300, since it is really a DirectX 9 part).   See the complete list [http://wiki.cchtml.com/index.php/9.4.]("http://wiki.cchtml.com/index.php/9.4") If your card is on that list, you are limited to open-source drivers on  Ubuntu Lucid. If you really need the proprietary Catalyst/fglrx driver,  you will have to use an older Linux distribution, such as Debian  Lenny/5.0.x or Ubuntu Hardy/8.04.x. See the complete list. So it will be using the open source driver.

Kind regards

---

### Post by Dsky on 2010-12-08
i tried 8.10 and it works but the release is no longer updated..

it's a problem..

how can i know what other distribution support it?

---

### Post by matt_symes on 2010-12-08
Hi

Other distributions? I'm not sure at the moment. ATI are not going to do any more work on the driver and it can't be used with the current kernels anyway. 

The open source community are continually developing one and it is a work in progress.

Could you open a terminal and type
[FONT=monospace]
[/FONT]```
[FONT=monospace]lspci -k | grep -iA2 vga
```

and post the results back.

Kind regards
[/FONT]

---

### Post by Dsky on 2010-12-09
```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
	Kernel driver in use: sky2
```

---

### Post by Dsky on 2010-12-09
but i've to understand why with ubuntu 9.10 with "normal" visual effect is all right

and if i try to update to 10.04,  with "normal" visual effects is impossible to use the whole system.. i've to set them to none and it's still not so fast

---

### Post by Dsky on 2010-12-09
with 9.10

> **Dsky said:**
> ```
 **lspci | grep -i vga**
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)

**dpkg -l | grep fglrx**
ii  fglrx-modaliases                     _2:8.660-0ubuntu4.1_                         Identifiers supported by the ATI graphics dr

** glxinfo | grep render**
direct rendering: Yes
OpenGL renderer string: Mesa DRI R300 (RV410 5653) 20090101 x86/MMX/SSE2 TCL


```

with 10.04 

```
dpkg -l | grep fglrx
ii  fglrx-modaliases                     _2:8.723.1_-0ubuntu5                              Identifiers supported by the ATI graphics dr


 glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI R300 (RV410 5653) 20090101 x86/MMX/SSE2 TCL _DRI2_

```

differences are underlined

---

### Post by matt_symes on 2010-12-09
Hi

You missed out the -k. Any chance you could repost that.

```
lspci **-k** | grep -iA2 vga
```I am not quite sure why 9.10 and 10.04 should be so different for you, although i am looking into it for you. It could be a whole host of things including the graphics driver. I think we can rule out KMS though.

What does top say is using your cpu?

One option for 10.04 might be to use the open source drivers from xorg-edgers, by adding the ppa and installing. They work on the open source drivers and, as the name suggests, are cutting edge but possible a bit unstable. I am reading up on it and will tell you what i think soon.

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

EDIT: Not sure they can be used on R700. They seem to be a work in progress for your chipset. 

[http://www.x.org/wiki/GalliumStatus](http://www.x.org/wiki/GalliumStatus)

In the meantime, if 9.10 is good for you i would continue to use that.

Hopefully someone else here will know something i don't.

Kind regards

---

### Post by Dsky on 2010-12-10
thanks so much

> lspci -k | grep -iA2 vga
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
	Kernel driver in use: radeon
	Kernel modules: radeon


i have 10.04 at the moment

---

### Post by efflandt on 2010-12-10
10.04 changed from user space video modules to kernel mode setting (kms), but older ATI cards (that I have) may not work too well with kms.  For example my desktop with X1300 had sluggish video and would not suspend/hibernate, and my work laptop with mobile X1300 would often have a boot video glitch that would make is hang.

A simple solution is **nomodeset** kernel boot parameter resolved those issues for me in 10.04.  Further explanation and how to add that to /etc/default/grub (use **gksu gedit** or **sudo nano** to edit that file) [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture")

9.10 or earlier did not use kms, and for some reason it does not seem to be a problem in 10.10.

---

### Post by Dsky on 2010-12-10
you were right... i tried changing the grub as u said and now the system is stable and fast even with "normal" visual effects!!

thanks a lot even if i didn't understand very well why this works.....

---

### Post by matt_symes on 2010-12-10
Hi

Well done efflandt. That was a good call. User space to kernel space KMS was the change. I am a bit confused though. Because from this document

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

there is this quote

> Customized configuration for X.org, the new way

Ubuntu Karmic Koala 9.10 and later supports Kernel Mode Settings (KMS) in ATI driver. This mode allows to automatically detect all necessary settings for your hardware, as well as to provide for better viewing experience. Notably, KMS eliminates "tearing" and "blinking" of video, including flash, and 3D windows, such as games. The configuration file xorg.conf is not required using KMS. 

This seems to suggest KMS was implemented in 9.10. Is it because the card is a legacy card, it needs user space KMS? Any info would be appreciated.

Kind regards

---

