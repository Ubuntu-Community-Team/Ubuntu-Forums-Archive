---
title: "Psychedelic colors"
date: 2024-04-13
forum: Hardware
---

### Post by hanserikstromberg on 2024-04-13
Hi,
I have a problem since about a year back. 
After upgrading from an earlier version of Ubuntu Desktop 20..something to version 20.04.06, all the colors are psychedelic and fuzzy on my TV.
More info:
Computer: HP EliteDesk 800 G3 Desktop Mini.
TV: Panasonic Viera TX-P50G30Y
I have connected a "Display port" to "HDMI" converter to the PC, and use a HDMI cable from the adapter into the TV.
I still have the same problem now using the latest Ubuntu version (22.04.4).
When I install Ubuntu, I get a question: "Try or Install Ubuntu", and if I there choose "Ubuntu (safe graphics)", everything during the installation looks ok (including the graphics), but after restarting, the graphics goes psychedelic again.
If I connect to a old computer display I have, I get the same problem.
If I connect to a semi-old computer display I have, everything looks fine (using the same cable and cable adapter).  
 I reckon, since it was working before (early version 20...) and it works when I choose "Ubuntu (safe graphics)". It should be possible to fix some how, but I need your help.

---

### Post by MAFoElffen on 2024-04-14
Yours should be using i915 driver for the Intel iGPU of the CPU... The "Safe Graphics" option uses "nomodeset", but you shouldn't really need that with that iGPU (normally). 

What does this say? Post the results within CODE Tags:
```

lscpu | grep -E 'Model name'
lspci -knnn | grep -A3 -E 'VGA|Display|3D'

```
I'm thinking it might have to do with going through the HDMI adapter, or if it is not really seeing the EDID of the TV.

---

### Post by hanserikstromberg on 2024-04-15
Hi,
Thanks for the help. 
```
lscpu | grep -E 'Model name'
Model name:                         Intel(R) Core(TM) i3-6300T CPU @ 3.30GHz
```
```
lspci -knnn | grep -A3 -E 'VGA|Display|3D'
00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 530 [8086:1912] (rev 06)
    DeviceName: Onboard IGD
    Subsystem: Hewlett-Packard Company HD Graphics 530 [103c:8055]
    Kernel driver in use: i915
```

I have tried two different adapters, both no-name (but from different suppliers), same result on both.
It is my first time posting in a forum (any forum), so I hope I'm doing things correctly, if not, let me know.

---

### Post by MAFoElffen on 2024-04-16
It's using the i915 driver...

With what kernel and what session type?
```

uname -r
echo $XDG_SESSION_TYPE

```
On the session type, does it help if you switch from wayland to X11 (or vice-versa) on login?

---

### Post by hanserikstromberg on 2024-04-17
I was apparently using Wayland. After a little googeling I was able to change to X11, but it did not help, it looked the same (I have now changed back to Wayland again).
```
uname -r
6.5.0-27-generic
```
```
echo $XDG_SESSION_TYPE
wayland
```

---

### Post by hanserikstromberg on 2024-05-04
An Update:
I have been spending some more time trying to fix the problem.
I have tested a third adapter, but with no luck. I do not believe the adapter is the problem anymore.
I have discovered that it works fine if I boot in "recovery mode". Although the resolution is not good enough for what I have planned, so I cannot always start in “recovery mode”.
I was able to change the resolution to 1024x768 (4:3) 75.03Hz. After doing that, the colors are still psychedelic, but I can just barely see whats going on, which means I can troubleshoot while I'm actually having the problem. 
I found somewhere that you could get driver information with the following commands:
 ```
sudo lshw -c video
 lsmod | grep intel

``` I used the commands both when booting normally, and when when booting in “recovery mode”. And it is a lot of differences, but I do not know what anything means.
If someone understand, and thinks the information can be of any help, I will post it.

---

