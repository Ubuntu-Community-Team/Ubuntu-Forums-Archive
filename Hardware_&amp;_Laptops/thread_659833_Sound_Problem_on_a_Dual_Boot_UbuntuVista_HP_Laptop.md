---
title: "Sound Problem on a Dual Boot Ubuntu/Vista HP Laptop"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by guren on 2008-01-06
Hi, I have an HP dv2600 laptop which is dual booted with Ubuntu Gutsy and Windows Vista.
My audio device is:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

My problem before was that I couldn't get sound working on my Gutsy even though the drivers were properly detected. I've tried many solutions from other threads including the ubuntu wiki [Gutsy Intel HD Audio Controller - Ubuntu Wiki]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller"). I thought this fixed it because the sound worked properly the next morning...after a restart? [well..no..after a shutdown].

My problem now is this. Although its a very light problem which can be ignored, I'm just curious why it's happening. Every time I try to boot to Vista and then try to **RESTART** to Gutsy, I get no sound. But if I try to **SHUTDOWN** and then boot to Gutsy, I get sound. Also, If I boot straight to Gutsy or restart from Gutsy after a straight boot to Gutsy, I get sound.

The bottom line is, why is it that I only get sound when I'm booting straight to Gutsy or when I'm booting Gutsy and not having to restart from Vista?

---

### Post by titi(ger) on 2008-01-07
Linux boots ignoring most of the bios settings.
Vista boots using the Bios settings.

So the irq settings and so on are different in linux and windows.
Probably the sound chip isn't properly reconfigured when rebooting.

---

### Post by cywfong on 2008-01-07
I have the same problem on my HP/Compaq Presario V3000.

---

### Post by guren on 2008-01-08
I'm using the latest bios drivers by the way.
I think that most users have this problem however it's not very visible to them.
I've seen threads where they say that the sound problem in gutsy is intermittent for some weird reason.
I'm guessing that this is the reason. They may have restarted from one OS to another and then they lost their sound because they came from another OS during restart.

---

### Post by thkatsou on 2008-02-11
same problem on an hp g5000 laptop with vista home basic and linux mint daryna 4.0. 
When you reboot into vista and after into linux there is no sound. Also noticed problems with keyboard not working.
If you shut down and then boot directly to linux there is no problem.

---

