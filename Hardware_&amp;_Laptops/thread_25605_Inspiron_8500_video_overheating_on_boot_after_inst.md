---
title: "Inspiron 8500 video overheating on boot after installing driver"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by Rehevkor on 2005-04-10
I recently installed Ubuntu on my i8500 and attempted to install the nVidia drivers for the Geforce 4 4200 Go. I tried installing from binary using apt-get, but the 3d acceleration would never work. I found a guide (cant find the link now) with instructions on how to compile the latest driver into the kernel as a module (forgive me if my wording is incorrect, I'm still pretty new to linux).

I followed the guide and managed to get the driver working with 3d acceleration. I went on to work on installing a wireless card driver, but after about 15 minutes the screen became corrupted and I was forced to power off. Attempting to turn the notebook back on resulted in a corrupted screen and no BIOS.

After some investigation, I found that the video card fan was no longer working. It would twitch a bit on start-up, but would not spin. I confirmed that the video card itself was still working by leaving the laptop alone for a couple days in a cool spot by the floor vent in my room. I was able to boot into Windows after letting it cool off, but about a minute later the corruption returned and it became unbootable again.

Is it possible that the compiled nVidia driver that I installed on Ubuntu somehow damaged or disabled the cooling on the video card? I haven't been able to boot the system for long enough to check much of anything, so I don't really have any other way to diagnose the problem other than what I've already done.

Any help figuring this out (and maybe even how to fix it) would be greatly appreciated.

---

### Post by c_dog on 2005-04-10
Seems to be something going on with APIC and APM. On my Compaq laptop, after a short while, the CPU frequency SpeedStep scaling will drop to the slowest speed and never kick the fan on.Things get a little toasty in very short order. Removing the 'powernowd' daemon will put the CPU back up to it's fastest speed. The fan now starts every now and then like it should.This problem has been re-occurring and going away with almost every other update for the past few weeks. Was working just before final Hoary, but final Hoary seems to have broke things again.

---

### Post by Rehevkor on 2005-04-10
Well, I can't even get this thing to POST, so there's something else going on here. I can't get into Ubuntu, or Windows for that matter.

---

