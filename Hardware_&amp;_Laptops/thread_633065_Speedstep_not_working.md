---
title: "Speedstep not working"
date: 2007-12-06
forum: Hardware &amp; Laptops
---

### Post by tisse on 2007-12-06
I'm running kubuntu gutsy and I just bought a new intel 2160 processor and a gigbyte motherboard. When I'm running winxp (gaming only...) the speedstep works, i.e. it reduces the clock multiplier from x9 to x6. When running kubuntu though the processor speed stays at the same speed all the time, i.e. multiplier set at x9.

It is not a portable computer but I want it to work to keep the power and temperature low. After reading some posts in this forum it seems that some have a problem where the multiplier is stuck at a lower speed, but this is not the case here.

Anyone have an idea how to fix this?

---

### Post by jespdj on 2007-12-06
I have different hardware than you on my desktop PC, but I had the same problem: my CPU was always running at 2.4 GHz.

My desktop PC has an Asus P5B Deluxe/WiFi-AP motherboard with a Core 2 Duo E6600, which should support x6 (1600 MHz) and x9 (2400 MHz).

I installed cpufrequtils:
```
sudo apt-get install cpufrequtils
```
With cpufreq-info I got an error message saying that CPU frequency scaling is not supported.

I looked in the BIOS setup and tried different settings, but this wouldn't solve the problem in Ubuntu. So I updated the BIOS of my computer and that fixed that problem, but now I had another one: the frequency is now stuck at 1600 MHz! Fortunately that was easy to fix with cpufreq-set:
```
sudo cpufreq-set -c 0 -u 2400MHz
sudo cpufreq-set -c 1 -u 2400MHz
```
Note that this is necessary for both cores (-c 0 and -c 1).
I haven't tried to reboot yet to see if it sticks... maybe I should put those commands in a startup script somewhere to make it work automatically after booting.

---

### Post by jespdj on 2007-12-07
I found out where I have to change it: Edit the file /etc/init.d/cpufrequtils:
```
sudo gedit /etc/init.d/cpufrequtils
```
There is a line:

MAX_SPEED="0"

Change this to the correct maximum speed, for example:

MAX_SPEED="2400MHz"

Reboot, and it works.

---

### Post by tisse on 2007-12-10
Thanks for that info. I already have the latest bios for my computer :(

I haven't tried the cpufrequtils though, will try it when I get home.

---

