---
title: "Ubuntu and Overclocking"
date: 2008-05-24
forum: Hardware
---

### Post by ShinHadoken on 2008-05-24
Well, it looks like I'm going to say bye-bye to Vista soon and hello Hardy! =D However, I do have a question. What is that best method for overclocking Ubuntu? I'm trying to avoid BIOS clocks, because my dad would throw a fit. I know there's gotta be some good softclocks for linux - anyone had any experience? What works best with Ubuntu?
 
Thanks,
 
SH

---

### Post by wdaniels on 2008-05-24
For GPUs, the main ones are [nvclock]("http://www.linuxhardware.org/nvclock/") for NVIDIA cards or [rovclock]("http://www.thinkwiki.org/wiki/Rovclock") for ATI's Radeon.

I'm afraid I don't know of anything for the CPU...I have a MSI board with CoreCell but never found any software to control it from linux :(

---

### Post by ShinHadoken on 2008-05-25
Thanks, but I'm looking at cpu clocks

---

### Post by ShinHadoken on 2008-05-25
bump

---

### Post by ShinHadoken on 2008-05-26
bump

---

### Post by TheLions on 2008-05-26
if you hadn't droped vista you can overclock it from there with Nvidia Control panel (if you have nForce chipset)...

---

### Post by pokkets on 2008-07-11
I've been into linux for about 9 months so I know enough to stay away from windows. I've just been learning things as I need them, which is fairly often. I'd be nowhere without ubuntu forums, and support. I don't know if you call it overclocking, I've been wondering what it's called and think it might be giving the same result. I hope someone can tell me if it's safe in case it burns out my cpu. Or someone else who tries it I'm using a HP dv9500t 2.2GHz with 4GB ram It seems well ventilated enough to avoid overheating.
I went  to Applications/System Tools/Ubuntu Tweak0.2/System/Power Manager/CPU Policy-performance value when on a/c. I found it when looking through the applications, and thought any tweak program should come in handy. I have no idea how well known it is.
 The default was a/c 85% on demand. I first increased it to 95%.with CPU frequency policy when on a/c at Performance. I'm folding@home. The work unit speed increased by about 20% I've kicked it up from 95% to 100%. At the moment the cpu is running about 60 deg C. Other programs and boot seem faster, but the FAH WU speed was a clear measure. I just found tweak 0.3.4-1, so that might be more useful. Hope it helps.

---

### Post by Rhubarb on 2008-07-11
What's so wrong about fiddling around in the BIOS to overclock your CPU?
(It's best to do this on a desktop computer, not a laptop).

The very worst that can happen is that you won't be able to boot up without resetting the CMOS jumpers / re-seating the battery on the motherboard.

Overclocking using software or the BIOS comes with exactly the same risks.
And those risks are quite minor (unless you've got a laptop - they can have problems dissipating heat).
Just so long as you know how to reset the CMOS memory you'll be fine.

---

### Post by zgornel on 2008-07-11
His dad would hear the beep-beeps and kick his a** :D . As for overclocking utilites in linux for CPUs, the are none! The only one was powertweak which I compiled from cvs a few years back when I had a Pentium MMX. If you have a 4 year old computer (or older), you can give it a try (probably it will not work, the last kernel it was tested on was a 2.5.x). Otherwise, use BIOS.

---

