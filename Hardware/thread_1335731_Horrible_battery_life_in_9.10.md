---
title: "Horrible battery life in 9.10"
date: 2009-11-23
forum: Hardware
---

### Post by Brii on 2009-11-23
I switched back to ubuntu a couple of weeks ago and got everything the way I want it. Excerpt for the battery life.

I used to get up to 3 hours with Windows 7, but now I only get an hour and a half.

Not sure if this is a contributing factor, but also, my CPU is always at 60%. 

Please help, thanks.

Here are my specs. I don't have any of the right drivers for any of the hardware though. Barely got it to go at 1370x760 res.

Acer Aspire One AO751h-1192 Specifications

    * Intel® Atom™ Processor Z520 (1.22GHz, 490MHz FSB, 512KB L2 Cache)
    * Genuine Microsoft Windows XP® Home (Service Pack 3)
    * 11.6-inch WXGA 16:9 ratio Acer CrystalBrite™ High Definition LED back-lit TFT LCD (1364 x 768 resolution)
    * Mobile Intel® US15W Express Chipset
    * 1024MB DDR2 533 MHz SDRAM Single Channel Memory
    * Integrated Intel® Graphics Media Accelerator 950
    * 160GB SATA 5400RPM Hard Drive
    * Multi-in-1 Digital Media Card Reader and Dedicated SD Card
    * Acer InviLink™ 802.11b/g Wi-Fi CERTIFIED®
    * Acer Crystal Eye Web Camera
    * Two Built-in Stereo Speakers
    * Three USB 2.0 Ports
    * 6-cell Li-ion Battery (5200mAh)
    * 11.18” (W) x 7.79” (D) x 1” (H)
    * Sapphire Blue
    * One-Year Standard Warranty

---

### Post by Brii on 2009-11-23
anyone? Help please =)

---

### Post by aaronchall on 2009-11-24
I really want to help, but I'm a computer noob myself, so this might just be a shot in the dark: 

First get the right drivers for your hardware. I understand that the wrong drivers can consume more energy.

Also, 1 gig of memory may mean your laptop is going to the swap partition on your hard-drive more often, especially if you have a lot of things going at once.  This wears on your hard-drive, and also uses up battery power every time the hard-drive spins up to access memory.  It also makes your programs run slower.  Type "free" in a console to see how much memory you're using, both before and after cache.  (Type "top" if you're running out of memory, and you'll see what's using the most at any given time, in case you want to try shutting down things...)

If I were you, I might consider it a high return investment to spring for more memory.

It might simply be that Windows 7 makes more efficient use of the cache and accesses your hard drive less, but now I'm speculating on things I don't know much about.  I hope this is somewhat helpful!

---

### Post by rastoboy on 2009-11-24
I know it's less than idea to have to do it, but you should really check out "powertop"--it's a commandline utility for finding out what is consuming power on your laptop.

You can disable functions you are not using.  Good drivers do this automatically.  

I have an ao751h and was just checking up on this forum to see how well supported it is now. :-)

---

### Post by Cheater512 on 2009-11-24
> **aaronchall said:**
> 1 gig of memory may mean your laptop is going to the swap partition on your hard-drive more often
...
It might simply be that Windows 7 makes more efficient use of the cache and accesses your hard drive less, but now I'm speculating on things I don't know much about.
Both are incorrect in this instance.

The first thing to do is to find out what exactly is using the CPU since it shouldnt be using 60% all the time.
That is your source of the power drain.

Use top or powertop to see what is using the most CPU (top of the list).
From there we can help figure out why that is occurring.

---

### Post by Brii on 2009-11-26
> **Cheater512 said:**
> Both are incorrect in this instance.

The first thing to do is to find out what exactly is using the CPU since it shouldnt be using 60% all the time.
That is your source of the power drain.

Use top or powertop to see what is using the most CPU (top of the list).
From there we can help figure out why that is occurring.

I don't know if this will help, but this is what happened:

     PowerTOP version 1.11      (C) 2007 Intel Corporation

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (100.0%)        1333 Mhz    87.5%
polling           0.0ms ( 0.0%)         1067 Mhz     0.0%
C1 mwait          0.0ms ( 0.0%)          800 Mhz    12.5%
C2 mwait          0.0ms ( 0.0%)
C4 mwait          0.0ms ( 0.0%)


Power usage (ACPI estimate): 9.0W (0.6 hours)

No detailed statistics available; PowerTOP needs root privileges for that

---

### Post by yossell on 2009-11-26
I second rastoboy's suggestion. My experience with powertop, it made all the difference. Like you, when I first changed to Ubuntu, I lost a lot of battery life. Running powertop and a minimal desktop environment, I'm now doing better than in windows.

All I do is run it as root - i.e. type "sudo powertop" from a terminal, and follow its suggestions from there. I keep the terminal running throughout the session, otherwise I think powermanagement ceases. By and large, it seeks to minimise the time that the chip runs at faster speeds. 

Run it, monitor the statisics (which will change depending on what you're doing) let us know and maybe we can help out.

---

### Post by Grenage on 2009-11-26
Sudo PowerTop, or just post the output of top here (order it by CPU; press "c" to do so).

---

