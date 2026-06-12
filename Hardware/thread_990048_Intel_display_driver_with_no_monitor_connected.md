---
title: "Intel display driver with no monitor connected"
date: 2008-11-22
forum: Hardware
---

### Post by nkskjames on 2008-11-22
I have the Intel D945 chipset and everything works great until I try to boot with no monitor connected.  I want to run X with no monitor connected so I can administer the machine remotely with "x11vnc".  The xorg log says there is no monitor detected so it loads the failsafe xorg.conf.failsafe.  If I set the driver to vesa in the xorg.conf, it works with no monitor connected but I would prefer to use the native driver.  I have also generated an xorg.conf with the Xorg -configure to see if it would not try to detect anything, but it still doesn't work.

Is there anyway to keep the intel driver from trying to detect a monitor or at least ignore the error if it doesn't find one? I have tried all the options in the intel man pages and none help.

---

### Post by krunge on 2008-11-22
> **nkskjames said:**
> 
Is there anyway to keep the intel driver from trying to detect a monitor or at least ignore the error if it doesn't find one? I have tried all the options in the intel man pages and none help.

Maybe hard-wire a monitor setting in xorg.conf:

```

Section "Monitor"
        Identifier      "hardwired 17-inch monitor"
        HorizSync       30.0-70.0
        VertRefresh     50.0-140.0
        Option          "DPMS"
EndSection

```

You may need to tweak the HorizSync/VertRefresh if you want a bigger resolution (I think the above will do 1280x1024)

---

### Post by nkskjames on 2008-11-22
> **krunge said:**
> Maybe hard-wire a monitor setting in xorg.conf:

```

Section "Monitor"
        Identifier      "hardwired 17-inch monitor"
        HorizSync       30.0-70.0
        VertRefresh     50.0-140.0
        Option          "DPMS"
EndSection

```

You may need to tweak the HorizSync/VertRefresh if you want a bigger resolution (I think the above will do 1280x1024)

When I did the Xorg -configure it created an xorg.conf that had a "hardwired" monitor section.  The intel driver still tried to look for the presence of a monitor and when it didn't find one, it went to safemode.

---

### Post by cariboo on 2008-11-22
I would suggest not using an X-server at all, and use X forwarding with a command like this:

```
ssh -X user@server
```

then at the prompt type:

```
sudo synaptic
```

the above command will run synaptic on your desktop, you can do this with any gui program without running an X server.

If this computer is to be a server of some sort, I would suggest using [webmin]("http://www.webmin.com/") to administer it

Jim

---

### Post by krunge on 2008-11-22
> **nkskjames said:**
> When I did the Xorg -configure it created an xorg.conf that had a "hardwired" monitor section.  The intel driver still tried to look for the presence of a monitor and when it didn't find one, it went to safemode.

That's too bad.  Are you sure the xorg.conf was referencing the "hardwired" section?

Since it sounds like you only want to access it via x11vnc, note that the vesa driver and ShadowFB=true has a chance of being a lot faster than the native intel driver. (since ShadowFB keeps the framebuffer in RAM that often speeds up x11vnc a great deal, sometimes 50X faster than native drivers.) But maybe there is some other reason you want to keep the native intel driver...

BTW, I'm sure you are aware there are other ways to do this that avoid the hardware graphics completely (e.g. vncserver, Xvfb, Xnest+xdmcp, ssh -X...)

---

### Post by maxim99 on 2008-12-26
I am looking for a solution to this problem exactly. Intel driver seems to not allow xorg to load, but vesa works fine. My situation is that the computer is on a projector, and the project isn't always on. I need to be able to boot the machine into X without the failsafe drivers loading, and using the Intel driver.

---

### Post by maxim99 on 2008-12-27
This appears to be an issue with the Intel driver itself. This bug here:

[https://bugs.freedesktop.org/show_bug.cgi?id=14611](https://bugs.freedesktop.org/show_bug.cgi?id=14611)

This explains the situation exactly. One of the developers proposes a possible patch for it. I hope that this makes it's way into the stable driver release as I don't know the the first thing about compiling a driver.

---

### Post by maxim99 on 2008-12-27
Using Jaunty (9.04 Alpha2), I did not encounter this issue. Seems the new driver version has addressed this issue and picks an output anyway. NICE!

---

### Post by Underpants on 2008-12-27
> **krunge said:**
> Since it sounds like you only want to access it via x11vnc, note that the vesa driver and ShadowFB=true has a chance of being a lot faster than the native intel driver. (since ShadowFB keeps the framebuffer in RAM that often speeds up x11vnc a great deal, sometimes 50X faster than native drivers.) 

What's the reccomended config for setting that up? sounds like something I could use in a few places.

---

### Post by krunge on 2008-12-29
> **Underpants said:**
> What's the reccomended config for setting that up? sounds like something I could use in a few places.

Edit /etc/X11/xorg.conf and put it in the Device section:

```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
        ...
EndSection

```

Your file will likely be different.  All I am saying is add or change the Driver setting to be "vesa".

---

### Post by Underpants on 2008-12-30
> **krunge said:**
> Edit /etc/X11/xorg.conf and put it in the Device section:

```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
        ...
EndSection

```

Your file will likely be different.  All I am saying is add or change the Driver setting to be "vesa".

EXCELLENT TIP!

LAN performance is about the same on a fast machine, but performance over the internet/ssh tunnel is 100 perfect faster. thanks for the tip!

---

### Post by krunge on 2008-12-30
> **Underpants said:**
> EXCELLENT TIP!

LAN performance is about the same on a fast machine, but performance over the internet/ssh tunnel is 100 perfect faster. thanks for the tip!

Interesting, I would have thought (and have observed in tests) that the LAN performance would show the biggest relative improvement.

The argument for this is that with a slow video card read rate (intel driver)  the card read time would be many times longer than the LAN send time.  But not so many times longer than the Inet send time.  So when you take a big bite out of the read time (vesa driver) you see a bigger effect for the LAN.  But it might be difficult to notice this.

Look for the measured video card read rate x11vnc prints out.

What I get for Xorg radeon driver:
```

30/12/2008 20:58:19 Autoprobing selected port 5900
30/12/2008 20:58:20 fb read rate: 10 MB/sec
30/12/2008 20:58:20 screen setup finished.

```

For vesa/shadowfb mode:
```

30/12/2008 20:58:55 Autoprobing selected port 5900
30/12/2008 20:58:55 fb read rate: 371 MB/sec
30/12/2008 20:58:55 fast read: reset wait  ms to: 10
30/12/2008 20:58:55 fast read: reset defer ms to: 10
30/12/2008 20:58:55 screen setup finished.

```

Which is almost a 40X speedup.

Since a 1280 x 1024 display at 32 bpp is about 5 MB of pixel data, the former takes 0.5 seconds (obvious pause) to read the whole screen, whereas the latter only takes 0.015 seconds (zippy).

If your rate is not > 100 MB/sec check that vesa enables ShadowFB mode (/var/log/Xorg.0.log), or force it in xorg.conf Device section with:
```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
        Option          "ShadowFB" "true"
        ...
EndSection

``` 

BTW, one can set "ShadowFB" "true" for most drivers, not just vesa.

This speeds up x11vnc a lot, but you lose 2D and 3D acceleration on the physical display (so most people wouldn't want to do this, but you said you are running headless.)

It is too bad one cannot turn ShadowFB off and on dynamically. I've never seen an Xorg driver give more than 15-20 MB/sec, but I have seen the proprietary nvidia drivers give 80-200 MB/sec, which gives you the best of both worlds.

---

### Post by Underpants on 2008-12-31
I just checked some things.

I went from 5mb/sec to 250mb/sec using the vesa driver. 

Thanks for the awesome tips!

---

