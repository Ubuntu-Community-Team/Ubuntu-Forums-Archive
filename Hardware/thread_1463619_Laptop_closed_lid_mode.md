---
title: "Laptop closed lid mode"
date: 2010-04-27
forum: Hardware
---

### Post by b1gdaddy87 on 2010-04-27
Hello guys,

I'm not sure if this has been addressed before, unfortunately I wasn't able to find the corresponding topic. 

I have a laptop sitting in a dock with the lid closed and an external monitor connected to it. Every time I accidentally open the lid, Ubuntu starts switching the display modes: mirrored, only laptop display, only external display. This is really bugging me and I'm looking for a way to disable this. 

Basically I need to configure Ubuntu to always turn off the laptop display when the lid is closed and AC power is connected. 

Looking towards your suggestions on how to tackle this.

---

### Post by Aearenda on 2010-04-27
Which release of Ubuntu are you using, and what is the video hardware? This may be hardware related rather than Ubuntu itself.

I think I would first try to set it to external only with the lid open, using the system->preferences->monitor utility (I think it was 'display' instead of 'monitor' in older releases). However, proprietary drivers such as Nvidia have their own tool for this.

---

### Post by b1gdaddy87 on 2010-04-27
I have a fujitsu siemens lifebook with intel integrated graphics and currently running Ubuntu 10.04. But was the same with 9.10, 9.04 and so on. Also I don't think it's a hardware related issue. When I used to run Windows XP on the same laptop it worked just fine while being docked.

---

### Post by Aearenda on 2010-04-27
The Intel graphics driver should work with the suggestion I gave above about choosing the preferred monitor. Did you try it?

---

### Post by b1gdaddy87 on 2010-04-28
I currently have my monitors set up in such a way that the laptop screen is turned off and the default display is the external monitor. However when I open the laptop lid it starts switching the modes between extended, mirrored and laptop screen only. There is no way to turn that switching off.

---

### Post by Aearenda on 2010-04-28
What happens if you hold the lid switch closed, if that is possible? I wonder if Ubuntu is misunderstanding the lid switch signal. It should be possible to get it to ignore the lidswitch, somewhere deep in udev - but I wouldn't know how.

---

### Post by b1gdaddy87 on 2010-04-29
Well I guess that's the only solution. But thank you very much for your help!

---

### Post by Aearenda on 2010-04-29
[This thread]("http://ubuntuforums.org/showthread.php?t=1076486") might give some clues on how to deal with it - I don't know how 10.04 changes things. The ACPI functions are still there, and looking into the lid.sh script suggests there is stuff there to work with.

Another thought - are there any BIOS settings that might be relevant?

And another: there is a command-line way to tell the driver which screen to use. For example, on my laptop, which uses Intel 945 hardware, this will switch the internal screen off and the external on:
```
xrandr --output LVDS1 --off --output VGA1 --auto
```
However, if the lid switch is being interpreted wrongly, the flipping will continue. I think I'd disable the lidswitch hardware!

---

