---
title: "Is there any way to disable hardware device at OS level?"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by pepclub on 2008-02-15
Been searching through some threads about the above question, seems there wasn't any proper answer for it. Thought I'd just ask again. 

Just to quote an unanswered thread: 
> **felicemcc said:**
> Hello fellows...

...  I need to disable the sound card. Before you ask, i have to tell you that I have an acer laptop and the BIOS does not allow to disable any integrated hardware.

Also before you ask about what specific model do I want to disable, i can tell you that i need to know this generic procedure, just like in windows you can open the Device Manager, highlight the hardware and use your mouse to simply click one button to disable it (Do you get the idea?). I don't care if to accomplish this i have to type 2.000 instructions, but i need to know how it is done.
...

Felice Candilio

Cheers.

---

### Post by mrsteveman1 on 2008-02-15
What you want to do is blacklist the kernel driver for this device. There isn't any way to keep Linux from SEEING the device, but you can certainly keep linux from loading a driver for it which would do the same thing. I routinely blacklist the PC speaker driver because it annoys the fsck out of me, beeping loudly at 4am because i hit backspace too many times. 

What you want to do this this: determine which kernel module your device uses in linux by checking lsmod, then add this name to the file /etc/modprobe.d/blacklist 

the lines look like this, for instance for the intel HDA sound driver:

```
blacklist snd-hda-intel
```

after you add a line such as that, the kernel will not autoload the driver even if it finds a matching chip in the system.

---

