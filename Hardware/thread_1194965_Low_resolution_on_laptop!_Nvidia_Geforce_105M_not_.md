---
title: "Low resolution on laptop! Nvidia Geforce 105M not recognised"
date: 2009-06-23
forum: Hardware
---

### Post by rajrambo on 2009-06-23
I'm using an Acer Aspire 5738G with 4gbDDR3 Ram and 320GB Hdd and NVidia Geforce 105M. I've tried installing Ubuntu 9 and 8.04.2 but both end up giving me poor screen resolution and obviously no enhanced graphics. The NVidia site doesn't have a unix driver for the GeForce G105M. HELP!!!!!!

---

### Post by fakewcfrog on 2009-07-23
There is a great application called Envy NG which finds the missing drivers for your nVidia/ATi graphics cards. It is available in Synaptic Package Manager as envyng-gtk. I recommend installing Ubuntu 9.04 for it.

---

### Post by swedishengineer on 2009-08-07
Does this solution work?  I'm running into the same problem on a new hp dv4t.  Is there a work around to let the windows driver work on linux, or is this even legal?

Thanks

---

### Post by Gillian00 on 2009-08-27
[http://www.nvnews.net/vbulletin/showthread.php?t=132041](http://www.nvnews.net/vbulletin/showthread.php?t=132041)

here is the solution


enjoy  :)

---

### Post by bsinger74 on 2009-10-26
I'm still digging.  Have a 105M in this Asus UX-50 laptop, tried envyng, tried the 192.32 beta driver from NVidia, tried the xorg.conf files posted here and other places in the forums, still getting: (II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Video Driver
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 0.99.3
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(II) NVIDIA dlloader X Driver  190.32  Wed Sep  2 03:17:55 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00@00:02:0
(EE) No devices detected.

Fatal server error:
no screens found

--------------------------------------

When I tried the envyng option, the whole keyboard/mouse input was lost in GDM.

Any other thoughts?  am I just missing something simple?

---

### Post by PantsOnFire on 2009-12-14
> **bsinger74 said:**
> I'm still digging.  Have a 105M in this Asus UX-50 laptop, tried envyng, tried the 192.32 beta driver from NVidia, tried the xorg.conf files posted here and other places in the forums, still getting: (II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Video Driver
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 0.99.3
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(II) NVIDIA dlloader X Driver  190.32  Wed Sep  2 03:17:55 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00@00:02:0
(EE) No devices detected.

Fatal server error:
no screens found

--------------------------------------

When I tried the envyng option, the whole keyboard/mouse input was lost in GDM.

Any other thoughts?  am I just missing something simple?

I am having the same issues/hell with my UX50. I cannot get the nvidia card to work at all no matter what I do. I just sits there dormant and unused.

---

### Post by mirelos100 on 2010-02-09
Hi, im waiting for my delivery of  **Acer **[COLOR=#313131]Extensa 5635ZG and it has Nvidia Geforce 105M and im quite unhappy with the post i`ve read about this video chipset ...it seems not recognized but do you guys get the error on windows linux? Do you think that on Xp windows will work ?i mean will it not give me the same error? Looking forward for your reply. Thx[/COLOR]

---

