---
title: "Nvidia control panel and drivers?"
date: 2013-06-23
forum: Hardware
---

### Post by argvar on 2013-06-23
HI, I'm new from windows, and I just installed Ubuntu desktop 13.04, and since I have Geforce 560 Ti video card I was wondering if Ubuntu installed the necessery drivers for it.

Granted my desktop resolution is correct, but I cannot find any indication in the System Settings > Displays that my video card is installed properly.

I also downloaded from nvidia some drivers package, but it has a file extension ".run", and Ubuntu treats it as a text file.

So, I have no idea what to do. Here's what I want:
- See what and if drivers are installed
- Install latest drivers
- Get access to nvidia's control panel

Any help is appreciated.

---

### Post by argvar on 2013-06-23
I noticed it says this:
"Gallium 0.4 on NVCE"

Clearly I don't have the correct drivers!

---

### Post by argvar on 2013-06-24
Wow, I've been googling how to install latest nvidia drivers in ubuntu... and this is a total mess. All pretty long pages with 50 lines of console magic to do, all with their own way of doing it, and all with a warning like "may make your computer not boot".

I don't want to be a whiner, but why does this have to be so complicated? This is the most basic thing people want to work, and geforce video cards are the most common video cards out there. I think Windows installs fresh with working geforce drivers, and all I get are ... gallium drivers which are something like software intermediate rendering.

That's it, I'm giving up on computers.

---

### Post by argvar on 2013-06-24
I'm on Ubuntu 13.04 64bit with geforce 560 ti.
I installed nvidia drivers from additional drivers found in "software & updates":
**nvidia-310 (proprietary, _tested_)**

It's working, but after rebooting my sound is gone!

But what appears to have happened is that the hdmi on my video card became the default audio device. I had to go to "sound settings" in the bar and set the analog output as default.

---

