---
title: "Cool n Quiet Issue - Abrupt Shutdown - Need Your Guidance"
date: 2008-11-14
forum: Hardware
---

### Post by quad65 on 2008-11-14
After much trial & error, I found out that Cool n Quiet was responsible for the issue I am experiencing.

If I disable Cool n Quiet, everything is fine. But I can't feel comfortable when I can't use something that I think useful. So, I need your help.

When Cool n Quiet is enabled, Ubuntu begins booting normally. Orange progress bar loads up, gnome kicks in and I see the background, gnome-panel and desktop icons are not there yet. At that particular moment, my PC shuts down. 

First of all, I would like to see if there is an error message popping up just before shutdown. I tried using Ctrl+Alt+F1, but I can't catch it because it happens fast.

I tried checking system logs, couldn't find anything that seemed relevant to me. (May be my lack of information.)

So, I'd appreciate it if you can help me find what is wrong here.

I have 2 solutions in mind that might work:

1. Updating BIOS's PST table. (I don't know how, disassembler may be needed, nearly impossible.)

2. There may be some way to hardcode the values* to powernowd or linux kernel. (I don't know how, again.)

* by values, I mean 2000MHz, 1000MHz etc. Which clock speed to run when the CPU is idle, which to use when under full load..

Any help is appreciated. Thanks in advance.

BTW: Mainboard: Epox 9NPA+ Ultra nForce4 Ultra Chipset Socket 939

---

### Post by doas777 on 2008-11-14
I usually just manually set my fans to 100% (at all times) and forget all the dynamic threshold stuff. it's handy if it works, but...

---

### Post by brandon88tube on 2008-11-14
How do you manually set the fan if there is no option in bios and nothing under /proc/acpi/fan ?

---

### Post by quad65 on 2008-11-15
> **doas777 said:**
> I usually just manually set my fans to 100% (at all times) and forget all the dynamic threshold stuff. it's handy if it works, but...

I'm more interested in scaling the CPU speed and voltage down rather than the fan speed.

---

