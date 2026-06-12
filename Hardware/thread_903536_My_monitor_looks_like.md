---
title: "My monitor looks like"
date: 2008-08-28
forum: Hardware
---

### Post by uid313 on 2008-08-28
I bought a Samsung SyncMaster 2493HM.

But it looks like ****.

How do I calibrate it?

---

### Post by overdrank on 2008-08-28
> **uid313 said:**
> I bought a Samsung SyncMaster 2493HM.

But it looks like ****.

How do I calibrate it?

Hi and have you tried the command ```
gksu displayconfig-gtk
``` and adjust there? What is the graphics card, if nvidia you can try and use the nvidia settings to adjust.

---

### Post by uid313 on 2008-08-28
displayconfig-gtk wasnt of any help. No callibration stuff there.

Yeah, its a Nvidia. GeForce 8600.

---

### Post by flakrat on 2008-08-28
exactly what do you mean by "it looks like ****"?

Also a few other questions:
 * Is the monitor connected using DVI or VGA
 * Does the display change if you wiggle the monitors video cable
 * Have you tried messing with the on screen display settings on the SyncMaster
 * Do you have the video set to a refresh rate that isn't supported by the monitor or isn't optimal
 * Is the display resolution set to something other than the native resolution for the SyncMaster? LCD's only look their best at their native resolution and refresh rate

I'm assuming that the video card is configured properly so that hardware acceleration works, etc? Maybe take a look at "glxinfo" output and verify that direct rendering is enabled and there aren't errors.

Just brainstorming here.

---

### Post by uid313 on 2008-08-29
It is connected over DVI.

But the brightness/contrast/luminance/gamma thing is bad.
The default settings are too bright and intensive.

So the colors does not look natural.

Refresh rate, display resolution, hardware acceleration are all good.

---

### Post by yaztromo on 2008-08-29
Just try opening a console and type

xgamma -gamma 0.75

You can experiment with other values too, I find 0.75 is right for my SyncMaster.

---

### Post by kpkeerthi on 2008-08-29
You can adjust colors using nvidia-settings (The control panel for nvidia)

To install,
```
sudo apt-get install nvidia-settings
```

---

