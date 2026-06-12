---
title: "Hardware problem - random shutdown"
date: 2009-12-24
forum: Hardware
---

### Post by rplantz on 2009-12-24
My desktop machine has a hardware problem. I suspect it's the motherboard but would like to hear other suggestions.

The machine is 4.5 years old.
   Motherboard: Abit NF8
   CPU: AMD64 3200+
   Graphics card: EVGA Nvidia GeForce 6200
   Memory: Kingston 1GB DDR 400
   Disk 1: SATA 160GB
   Disk 2: IDE 80GB
   OS: Ubuntu 9.10, amd64

Symptoms:
1. The most common one is a random, sudden shutdown. It's as if the power was turned off, except the power LED on the motherboard remains on. The machine sometimes runs for hours, sometimes it won't even completely boot. According to the BIOS "PC Health Status" all the voltages are within 5% and the temperatures are normal.

2. Less often, the icons on the desktop become blank squares. I can move open windows with the mouse, but windows will not close. I have to use the power button to shut down.

3. I usually hear a single short "click" just before a problem occurs. It's very short and barely audible.

Things I have tried:
1. Disconnecting one disk and doing a fresh install on the remaining one. I've tried this with both disks.

2. Running from an Ubuntu live CD.

3. Reseating all the connections inside.

It seems to run okay with only the BIOS running, i.e., no disk involved.

My take is that something in the disk controller hardware on the motherboard is broken.

Any other ideas?

---

### Post by Ayuthia on 2009-12-24
Does dmesg report anything?  You might need to go into /var/log/dmesg.0 to see what happened in the previous log (provided that it was the previous boot that had the crash).  It might tell you something.

---

### Post by Fir3chi3f on 2009-12-25
I had these same symptoms on two computers at one point. My laptop would randomly shut down because of over heating and my desktop because of a cheep failing power supply.

What kind of power supply are you running? and I would try cleaning it out with some compressed air first.

---

### Post by IcarusR on 2009-12-25
Could also be faulty memory.
Have you tried running memtest from grub menu ?
Can you try a different memory stick, from another machine ??

---

### Post by rplantz on 2009-12-25
Thanks for the replies.

I have cleaned all the dust out. I had that problem a couple of years ago. The CPU heat sink was completely clogged with dust.

I have not looked at /var/logs/dmesg.0. I'll see if I can get the system to stay up that long.

I tried the grub memory test once, and the system powered down in the middle of it.

I'm going to try a new power supply today or tomorrow.

--Bob

---

### Post by IcarusR on 2009-12-25
CPU heatsink blocked will make cpu over heat & system will become unstable & eventually fry cpu. Hopefully yours has been shutting down before cpu damage.
I have to clean my server out every seven months or so for this reason.
If no better try another cpu, incase yours is damaged.
I would test it properly before buying new psu.

---

### Post by rplantz on 2009-12-28
I replaced the power supply. My system has been running flawlessly for nearly two days, so I think that solved the problem.

I note two things:

1. The new power supply is **much** quieter. I don't think I realized how noisy the old one had become over time.

2. I did not know that the power supply has something in it that can make a "clicking" sound. It's been over 40 years since I designed a couple of power supplies (one for the Gemini space capsule, the other for the LEM). They were both pure solid state. Not to mention that the technology has changed since then. So I started by working with the disks, assuming the clicks came from one of them.

Thanks again to those who contributed.
--Bob

---

