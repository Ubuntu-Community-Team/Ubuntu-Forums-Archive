---
title: "Screen + i915 driver + bad color"
date: 2013-11-01
forum: Hardware
---

### Post by skapinthefourb on 2013-11-01
Hi everyone, 
I just have bought a 12" LCD touch-screen no-name (egalax for touchscreen).
I manage to make the touchescren works well (xinput_calibrator+some edit about invertX/Y)
But after tons of day working on screen setting, I coulnd't figure out out to fix my issue.

My screen display some ugly/bad color. Instead of smooth color gradiant, I have ugly color, when imove windows, i can see some bad color sometime, and the pxiel are getting uglier every hours the screen is on.
The screen works perfect on Windows. My computer works perfect with different screen. So it's NOT a 100%hardware issue, but more a driver/compatibility.

I'm using a Intel pentium G2030 as CPU, with integrated GPU. Using intel i915 driver.

I 1st thought it was color depth issue, so i started my XServer as 16b and 8b, but nothing, just uglier...

I tried blacklisting i915 driver, but bothing change.

All help is welcome here, and thanks a lot, really. I mean i'm stuck and i don't know which way to take, how to resolv this....

---

### Post by sudodus on 2013-11-03
Welcome to the Ubuntu Forums :-)

This tweak works for some Intel graphics: Edit (or create) [FONT=courier new]**/etc/X11/xorg.conf**[/FONT] as follows: (there should be a ***tab*** in the beginning of each line except the first and the last).

```
Section "Device"
 Identifier "Intel Graphics"
 Driver "intel"
 Option "AccelMethod" "uxa"
EndSection
```

---

### Post by skapinthefourb on 2013-11-11
I love you, thank

It's strange cause my screen didnt work, but sometime (after soem time) he went well. For no reason. I first tought it was some kind of update or something but no...

So I tried with your solution, till now it is okay.

So thank you sudodus !

I thin linux swapped to another driver/method (like the tweak) automatically after some time. No other reason imo.

---

### Post by sudodus on 2013-11-11
I'm glad it works for you now :-)

In order to help other people find the solution, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

---

