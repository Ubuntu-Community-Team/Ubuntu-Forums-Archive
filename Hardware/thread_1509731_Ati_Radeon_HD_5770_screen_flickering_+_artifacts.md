---
title: "Ati Radeon HD 5770 screen flickering + artifacts"
date: 2010-06-14
forum: Hardware
---

### Post by Roisack on 2010-06-14
I recently decided to upgrade my hardware and took a small risk by purchasing an ATI card.

Here's my hardware

Asus P6X58E-D
Core i7 930 2.8GHz LGA1366 BOXED
Ati Radeon HD 5770 CuCore, 1GB GDDR5
3x2GB, DDR3 1600MHz, CL9
Using the latest ATI drivers: ati-driver-installer-10-5-x86.x86_64
Running Ubuntu 10.04 64-bit

The problem is as follows:

My screen flickers with some applications such as the screensaver, Blender 3D and Guild Wars. It seems as if the windows don't know whether they have to be rendered on top or below the other windows at the same location. Screensaver then is a mess on my wide screen monitor while my other monitor shows it fine. Also, when I close the screensaver it doesn't show the password box as it's most likely hidden behind the bugging screensaver. I have to type my password blindly.

The problem might be related to using dual screens as the screensaver only bugs on one of my displays.

If I had dual screens plugged in during Ubuntu install I didn't see anything on my wide screen monitor. At my left monitor (monitors positioned as shown in the video below) I saw the default wallpaper so that it was way too left - half of the screen was black. I performed the install using the alternative install (text mode).

This is probably a wine bug, but Guild Wars also crashes at game load. Let's not worry about this.

Here's a video of the problem: [http://sianleuka.ath.cx/~gekko/radeon_hd_5770_flicker.avi]("http://sianleuka.ath.cx/~gekko/radeon_hd_5770_flicker.avi")

I'm not that experienced in Linux yet, so be verbose on your help if it isn't that much of a trouble.

---

### Post by MrSqueezles on 2010-06-16
I have the same issue with ATI Mobility Radeon HD 3400.  I'm sure it's a problem with the proprietary ATI drivers.  I'm going to try the open drivers to see whether the problems goes away.

---

### Post by MrSqueezles on 2010-06-16
The open drivers fixed the problem.  Now I have a decision to make.  Do I accept slower 3D performance to have dual monitor screensavers?

---

### Post by Roisack on 2010-06-16
I figured out that the problem occurs if I start applications by running them from the console, whatever the reason for that may be. My applications no longer flickered if I went to preferences -> appearance -> visual effects and set them to none.

Screen saver was still bugging though. I then tried this: [http://www.webupd8.org/2010/04/how-to-enable-direct2d-acceleration-in.html]("http://www.webupd8.org/2010/04/how-to-enable-direct2d-acceleration-in.html")

And then set the effects on again - no flickering. Screen saver still bugs, though. I don't think I'll be going for the open drivers for the screen saver if wine works.

---

