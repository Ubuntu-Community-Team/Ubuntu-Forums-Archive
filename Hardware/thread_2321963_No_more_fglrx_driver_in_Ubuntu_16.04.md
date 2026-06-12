---
title: "No more fglrx driver in Ubuntu 16.04 ?"
date: 2016-04-25
forum: Hardware
---

### Post by cogset on 2016-04-25
So, reading the release notes for Xenial [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)
I've learned that the proprietary fglrx driver will no longer be used :

> The fglrx driver is now deprecated in 16.04, and we recommend its open source alternatives (radeon and amdgpu). (...)

When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware). 
That worries me : the open source driver is a no go for me, I've  been (reluctantly) using the proprietary fglrx driver simply because it works better - with the open source driver, I'm not even able to fine-tune the display, all I can do is to rely on some xrandr commands to somehow adjust (very crudely) brightness and gamma.

On the other hand, I know nothing about the new  AMDGPU drivers, and  I'm afraid they might not be available for oldish ATI cards , such as my Radeon HD 5430.

So, when the time comes to switch from 15.10 to 16.04 (I always prefer LTS releases, 15.10 was a fallback) , what will happen? 
Will I be forced to just switch back to the "old" open source driver and live with it, unless I buy a more recent video card?

Is there a chance that new AMDGPU drivers will work with my video card, and how different they are from the current open source radeon driver?

---

### Post by QIII on 2016-04-25
Hello!

This is going to be a turbulent year for AMD users.  AMD is giving us exactly what we have been asking for:  a genuinely useful open source driver.  But that will come with some pain.  Bear in mind that AMD also has to work in its future plans for the driver and keep in line with Khronos' Vulkan API -- the future of graphics APIs.  AMD has a lot on its plate.  The dust is expected to settle by about August.  Unfortunately, by then your 15.10 will no longer be supported.  14.04, however, will -- and it will still have the fglrx driver.

For a bit of back info, you may be interested in this [Phoronix article]("http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-16.04-Dropping-fglrx").

When I installed 16.04 with an R9 290X (Hawaii -- which is a Sea Islands chip), the RadeonSI driver was automagically used.  When I installed it with an R9 380X (Tonga -- one of the Volcanic Islands chipsets), the AMDGPU driver was automagically installed.

AMDGPU has been performing very well for me. Another Phoronix article says it works about 90% as well as the fglrx driver.  However, it does not have the AMDGPU Pro overlay (the proprietary bits will be on top of the common AMDGPU (mostly) open source bits) so I am not sure if things that require the proprietary driver will work.  In fact, even with AMDGPU Pro, I'm not sure it is guaranteed that everything designed to use fglrx will work.

My recommendation:  Unless you have a Volcanic Islands chipset (Tonga and Fiji), back up to 14.04 and grit your teeth through the Summer (or Winter if you are antipodean) and hope AMD comes up with the goods.  Supposedly, fglrx will return with the first point release of 16.04 (16.04.1), but I'll believe that when it happens.

---

### Post by him610 on 2016-04-25
FWIW, I have an AMD Athlon 5350, integrated APU/GPU, that normally runs 14.04 using the fgrlx driver without issues. Yesterday, on the same system, I booted into Xubuntu 16.04 from a USB stick. I noted it was using the Radeon driver that came with the Ubuntu 16.04 distribution. I normally don't run applications that stress the GPU - no gaming, just browsing the web with several tabs open along with a terminal window, gedit, the file manager, and software center. There did not seem to be any issues with the Radeon driver

---

### Post by cogset on 2016-04-26
Well I'm not saying the radeon driver doesn't work at all, in fact I've used it and still use it in some installations: but it's certainly not my first choice, starting from that:

   > I'm not even able to fine-tune the display, all I can do is to rely on some xrandr commands to somehow adjust (very crudely) brightness and gamma.

the feature I like the most of the fglrx driver is indeed its control panel, where you can finely adjust several parameters (brightness, contrast, saturation, white balance etc.)  which -as far as I know- are out of reach of the radeon driver abilities.

What can be achieved with xrandr is very coarse and not even remotely comparable to what the fglrx driver can do.
Unless there is some other way to fine tune the display (without the fglrx driver) that I'm not aware of.

---

### Post by cogset on 2016-04-26
> **QIII said:**
> 
This is going to be a turbulent year for AMD users.  AMD is giving us exactly what we have been asking for:  a genuinely useful open source driver.  But that will come with some pain. 

True that ;) looks like we're going to get what we always asked for...

> **QIII said:**
> 
My recommendation:  Unless you have a Volcanic Islands chipset (Tonga and Fiji), back up to 14.04 and grit your teeth through the Summer (or Winter if you are antipodean) and hope AMD comes up with the goods.  Supposedly, fglrx will return with the first point release of 16.04 (16.04.1), but I'll believe that when it happens.

I forgot to say that I'm using Ubuntu-MATE 15.10 because there was no official 14.04 version: so I really have to upgrade to Xenial when the time comes, since there is no 14.04 (official) MATE version to get back to.
That, however
> Supposedly, fglrx will return with the first point release of 16.04 (16.04.1), but I'll believe that when it happens.
is interesting news, where did you learn about it?

---

