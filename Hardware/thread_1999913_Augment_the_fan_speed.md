---
title: "Augment the fan speed"
date: 2012-06-08
forum: Hardware
---

### Post by forevertheuni on 2012-06-08
Hi. I own a LG S510 that was a bit warm.
I cleaned everything and changed my thermal paste.  Now the cpu is real cool. The problem is, the fan is spinning accordingly to the CPU temp. And since this is a laptop it makes the GPU stay really hot since it needs a bigger push from the fan.  Once the cpu gets a bit warmer the fan starts to spin and the GPU comes down to acceptable levels.
Is there any way to increase the FAN speed? Or to make them spin harder at a lower CPU temp?
What info should I provide? DSPT?

---

### Post by Redblade20XX on 2012-06-08
First look into your BIOs and see if there is anything you can adjust for the fan such as temp trip points, fan always on, etc. Usually stuff like this are in an advance menu for your BIOs.

-Red

---

### Post by forevertheuni on 2012-06-22
> **Redblade20XX said:**
> First look into your BIOs and see if there is anything you can adjust for the fan such as temp trip points, fan always on, etc. Usually stuff like this are in an advance menu for your BIOs.

-Red

There is nothing. It's a laptop I can only change the date(I'm exagerating)

---

### Post by Redblade20XX on 2012-06-22
> **forevertheuni said:**
> There is nothing. It's a laptop I can only change the date(I'm exagerating)

What graphics card do you have? Do you have the open source one installed or the proprietary one installed? Usually the proprietary one has better thermal controls.

-Red

---

### Post by ivotkl on 2012-12-02
Hello, I have no BIOS fan control options. I own a Lenovo G550, with Intel GM45 integrated graphics.
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
```

I once tried to install proprietary drivers, but Intel' s page has now a link for intellinuxdrivers, which is a website for open source intel drivers.

Now, back to the topic, this is the driver Mesa installed:
```
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20091221 2009Q4 x86/MMX/SSE2
OpenGL version string: 2.1 Mesa 7.7.1
OpenGL shading language version string: 1.20
OpenGL extensions:
```

I' ve seen a rather full-of-steps procedure for fan-speed control that apparently does the thing, but it was created for Oneiric and I run Lucid.

---

