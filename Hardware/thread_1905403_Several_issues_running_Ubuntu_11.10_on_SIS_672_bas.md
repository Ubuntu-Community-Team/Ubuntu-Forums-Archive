---
title: "Several issues running Ubuntu 11.10 on SIS 672 based laptop"
date: 2012-01-06
forum: Hardware
---

### Post by MaxPayneFH on 2012-01-06
I recently installed ubuntu 11.10 (x64 version) alongside windows vista on an old laptop and faced several problems: :(

1: The laptop doesn't shut down property -> the screen flashes and flickers alot during shut down procedure, until the display finally turns off but the power led stays on and I can ear the computer working, so I have to press the power button for some secs to force the computer to shut down.:-?

Strangely restart works, the screen flashing show still happens but eventually after a while the laptop restarts.

2: the mouse cursor disappears instantly if I'm not moving it or blinks if moving slowly, this bug however doesn't occurs on the desktop backgroud itself, only on top of programs like firefox or on top of nautilus and system settings.

3: On windows the max supported resolution is 1280x800, while on ubunto resolution is capped at 1024x768.

I tried the instructions on this thread:

```
http://ubuntuforums.org/showthread.php?t=1370258
```

but I had a problem on step 3

4: No support for the 3D version of unity, but the hardware should be capable of supporting, if a proper driver is available, since it supports aero on vista.
But this is no big deal.

Additional hardware information:

Model: Insys M746S 
 
CPU: Intel Pentium T3200, 2x2ghz, 1mb, 667mhz 

North Bridge: SiS 672(fx) 
South Bridge SiS 968 
 
IGP: mirage 3 graphics 
 
Sound Card: Realtek ALC662 
 
RAM: 4gb ddr2 667mhz cl5 
 
HDD: Hitachi 320gb

If anyone could help me with any of these issues, especially the shutdown problem, I would be really grateful.

---

### Post by MaxPayneFH on 2012-01-11
I just found out shut down works if the power cable isn't connected to the laptop:P, its an improvement but it simply makes this bug look even more stupid.:mad:

---

### Post by carlosb1504 on 2012-01-22
I am having the exact same issues. same gpu. same mouse flicker and resolution cap. any advice? Ive tried a method involving a sisimedia driver which just makes the system hang at the splash screen. i think that procedure only works in earlier ubuntu versions.

---

