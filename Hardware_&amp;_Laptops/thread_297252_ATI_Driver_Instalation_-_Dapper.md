---
title: "ATI Driver Instalation - Dapper"
date: 2006-11-10
forum: Hardware &amp; Laptops
---

### Post by core on 2006-11-10
Hi,

I've been trying to install the drivers for my ATI graphics card but no sucess so far. It's a Radeon Mobility 9100IGP.

I've followed the instructions from [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide), but still no sucess.

fglrxinfo always returns this:
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

and dmesg | grep fglrx output is:
```
[17179618.344000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179618.348000] [fglrx] Maximum main memory to use for locked dma buffers: 402 MBytes.
[17179618.348000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[17179620.080000] [fglrx:firegl_init_mask_ram] *ERROR* maskram_type not detected
[17179620.080000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179620.080000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179620.084000] [fglrx] AGP detected, AgpState   = 0x1f00021b (hardware caps of chipset)
[17179620.084000] [fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
[17179620.100000] [fglrx] total      GART = 67108864
[17179620.100000] [fglrx] free       GART = 51113984
[17179620.100000] [fglrx] max single GART = 51113984
[17179620.100000] [fglrx] total      LFB  = 28307456
[17179620.100000] [fglrx] free       LFB  = 22016000
[17179620.100000] [fglrx] max single LFB  = 22016000
[17179620.100000] [fglrx] total      Inv  = 0
[17179620.100000] [fglrx] free       Inv  = 0
[17179620.100000] [fglrx] max single Inv  = 0
[17179620.100000] [fglrx] total      TIM  = 0

```

Any ideas? I've ran out of them, and giving up on Dapper just because of this is shameful but I'm getting stuck with no other choice.

Thanks.

---

### Post by ReaderRat on 2006-11-10
You may find help  [**[color=RED]HERE[/color]**](http://www2.ati.com/drivers/linux/linux_8.8.25.html)

---

### Post by core on 2006-11-15
Thanks. There it says the drivers supports only 2D features for my graphics card.
Still, what bothers me is that when I first installed dapper, it was all ok, google earth and glxgears were running smoothly. It all got mixed up when I tried to install ATI drivers (still dunno why) following instructions from the wiki. And unninstalling the way the say at the wiki does not fix it back either.

I'm a little stuck here, I don't wanna mix up the X11 configs whitout knowing what i'm really doing.

Any advices? Thanks again.

---

### Post by bonzini on 2006-11-17
I'm not positive on this, but I think your problem is that you don't want the fglrx driver, you really want the ati driver (which doesn't come from ati, it's an open-source driver).

Go to the wiki and try reading "radeon" and "CompositeManager/AIGLX".  These have some speed-up tips for your ati driver and Mesa OpenGL.

I have what sounds like the same problem you have - my ATI chipset's DRI is not supported by ATI's drivers (those are the fglrx drivers).

Good luck!

---

### Post by Dale61 on 2006-11-17
I also got sucked in to installing the fglrx driver as I wasn't getting 3D, and once installed, the next reboot got me the dreaded 'Xserver has failed' blue screen.

Tried a couple of different settings without getting a result, so went back to the thread outlining how to restore xserver after that dodgy update was released (August?).

I first downgraded to 10.2, and got the gui back, then was prompted to update to 10.4, and low and behold, I now have 3D rendering.  WOOHOO.

Sometimes, upgrading isn't always the best thing to do.

---

### Post by core on 2006-11-24
Thanks for the tip, but all didn't find a DAPPER tutorial to uninstall the fglrx driver. Just by doing apt-get remove of the driver, X got messed up, and I could restore it only by reinstalling the fglrx driver.

How can I get rid of it? Thanks.

---

