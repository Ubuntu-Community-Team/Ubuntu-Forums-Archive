---
title: "S-Video to TV using Ubuntu 9.10 and Radeon 9500pro"
date: 2010-01-27
forum: Hardware
---

### Post by DTM84 on 2010-01-27
Hi. My ultimate goal is to stream Hulu on my TV. 

I've had success with windows, but can't get Ubuntu to do it.

Doesn't seem that Ubuntu 9.10 picks up the TV as a monitor automatically. There are a number of threads touching this topic, but I haven't found a definitive solution. 

My system specs are:
Asus AV8 Delux
AMD Athlon(tm) 64 Processor 3000+
512MB RAM
320GB SATA
80GB IDE
ATI Radeon 9500Pro 128MB

The solutions I've seen in the forums include:
Changing the resolution
Changing the Bios Configuration
Configuring xorg
Downloading the proprietary ATI drivers

I tried the first two, being the easiest, but changing the resolution didn't help and my bios doesn't have any S-video options to change.

I've seen forums hint that the ATI drivers are not supported in 9.10, but if anyone has any more info on this I'd appreciate it. The drivers won't work for me, and when I load them it wont give me a GUI upon boot up. 

I'm a little worried about configuring xorg, and I wanted to post this before I tried. 

Thanks

---

### Post by DTM84 on 2010-01-30
Does anyone have a soultion to this or does anyone know what is going on with the ATI propriatary drivers for 9.10?

---

### Post by DTM84 on 2010-02-02
Anybody? Did I post this in the wrong section?

---

### Post by batnas on 2010-02-28
try:

[https://wiki.ubuntu.com/X/Config/SVideo]("https://wiki.ubuntu.com/X/Config/SVideo")

---

### Post by DTM84 on 2010-02-28
This looks like it is going to work for me. I think I am going to have to add some resolution settings to xorg in order for it to work completely properly, but all in all a good fix. 

Thanks a bunch!

---

