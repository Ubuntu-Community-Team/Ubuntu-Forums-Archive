---
title: "Learning to Optimize Hardware Compatibility"
date: 2011-11-15
forum: Hardware
---

### Post by nik1979 on 2011-11-15
Hi everyone, 
I have a graphics card that is un-utlized. I tried using nvidia Drivers using the "safe methods" but both made things worse. When newly installed it was blinking occasionally and 1024x768, then it became 800x600 with the first nvidia driver installed. I tried the "non-recommended" option then it got worse 640x480. 
[IMG]https://lh6.googleusercontent.com/-XKhOMSaLqfI/TsLOlBoDHKI/AAAAAAAABtg/tX7OYjxshaI/s400/Safe%252520Hardware%252520Drivers.jpg[/IMG]

I then went back to default. Searching for a new fix, I found out about xrandr ([https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)) and used that method of adjusting the screen size. It worked. I also tried trying to apply what I learned installing the nvidia, but resolution was locked on 800x600 and 640x480. 

Right now I'm using the xrandr fix, but it kind of "stretched" my monitor. 
[IMG]https://lh3.googleusercontent.com/-mHEjbOcLmto/TsLNdYIHs0I/AAAAAAAABtQ/0hRgbw3n7_8/s400/xrandr.jpg[/IMG]
About 2 years ago, a friend helped me out by walking me through Kernel compilation to have the same graphics card work for 64bit Ubuntu 9.10 that worked but we are both busy for him to repeat that and I'd rather be self sufficient and learn what exactly he walked me through. 


Thanks in advance, 
Nik

```

UBUNTU 10.04.3
Desktop
Pentium Dual-Core E5200 @ 2.50GHz
Passmark 1,664
4GB PC3 KVR1333D3N9/4G
MSI G41M-P28
Intel® G41-based mainboard
- Supports FSB 800/1066/1333 MHz
- Supports two DIMM DDR3 800/1066/1333*(OC) DRAM
- 4 SATAII ports and 4 rear USB 2.0 ports
- 7.1 channel audio output
Graphics Card 
nVidia Corporation G94 [GeForce 9600 GT] 512MB

Monitor 21.6 inch VA2226w View Sonic 1680x1050 

```

---

### Post by dabl on 2011-11-15
If you are using the "Recommended" driver, which I would also recommend, then do Alt-F2 "gksudo nvidia-settings" with no quote marks.  This should open the nvidia-settings utility.  If it does not, you may need to install nvidia-settings.

With nvidia-settings open in super user mode, adjust the screen resolution as you need it.  Leave the refresh rate set to "auto".

When you finish setting the resolution, click the button in the lower right of the window that says "Save to X Configuration File".  That will make the settings permanent.  Then you can exit nvidia-settings.

---

### Post by nik1979 on 2011-11-26
Thanks Dabi,
Sorry for the late reply I've been trying to do this all sorts of ways. 

Anyway, I've done what you suggested but there is a Limit, a cap to the resolution. 

In the past weeks I've been researching this on and off and it seems there is no quick and easy solution because of the variety and age of graphics cards out there. 

It seems I have to really need to try to digest that massive Readme in the NVIDIA website. Too bad they don't have a PDF of the README thats updated to 2011 (the txt files are really old, one I found is 2001). 

I'll try to share my notes if I make headway.

---

### Post by jocheem67 on 2011-11-26
You could do a 

>  lspci -vnnn | grep VGA 

to get the details 'bout your adapter, or just skip the 'grep' part in that command. It'll give you a lot of info that's truly googleable...
You might have to force the reight resolution and refreshrate through a custom nvidia.conf. I'm not sure where that one should go nowadays though.
I believe it should be in /usr/share/X11...there's probably more info on your card on the web..
You could check the Arch and Gentoo wiki's > they're probably the best ones.

---

### Post by nik1979 on 2011-12-04
I gave a really good ole try, but no success. 
I'll take a break untill I get another SATA HDD installed, that way i can experiment in a seperate OS and not lose my whole system when I try these.

---

