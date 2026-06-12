---
title: "Lag on an i5 2520"
date: 2011-05-14
forum: Hardware
---

### Post by jmknsd on 2011-05-14
I just got a Lenovo T420 (no discrete graphics) and put 11.04 on it. Everything is great, but there seems to be a bit of lag, just a few seconds fairly randomly. Not a major problem, but this is a fairly powerful laptop. 

Also, Totem seems to choke on 1080p and 720p video, with the video and sound desyncing and the video getting garbled occasionally. VLC works fine though.

I asked on IRC, and someone told me I needed to install the Intel graphics drivers, but I am pretty sure they are open source and are already included.

Is this something that everyone is facing with sandy bridge, and will improve over time, or is there something else I need to do?

---

### Post by PhantmKllr on 2011-05-14
Even though 11.04 is a stable release, there are still a lot of problems to work out of it. I would think that your problems will vanish when 11.10 releases, or sooner when updated are released.

Plus, the HD Graphics 3000 chipset (default on T420) is a relatively new product, so there may be a few graphics updates down the line which should address the video playback issues.

---

### Post by jmknsd on 2011-05-14
> **PhantmKllr said:**
> Even though 11.04 is a stable release, there are still a lot of problems to work out of it. I would think that your problems will vanish when 11.10 releases, or sooner when updated are released.

Plus, the HD Graphics 3000 chipset (default on T420) is a relatively new product, so there may be a few graphics updates down the line which should address the video playback issues.

Yeah, that's kind of what I expected to be the case. The lag is easily tolerated, and it might go away when I stop using a second monitor.

---

### Post by PhantmKllr on 2011-05-14
Yeah, I've noticed a few problems when using more than one monitor with 11.04, especially with integrated Intel graphics.

---

### Post by slooksterpsv on 2011-05-14
A few things you can try:

1. Install compiz configuration settings manager (CCSM), open it up and click on OpenGL, then uncheck the VSync option

2. Go to System Settings -> Monitors and make sure your Hz is set to 60 and not auto.

3. Open Additional Drivers and make sure there's not an additional drive you can install.

---

### Post by coober85 on 2011-05-15
I have a t520 too,

I'm currently in the process of installing Linux Mint 11 RC, but I've had Windows 7 "with Lenovo enhanced experience 2.0" to start off, and I can say that I've complained of the exact same thing.

it's not awful, but in throwing down $$$ for a new comp, I expect it to be flawless with

---

