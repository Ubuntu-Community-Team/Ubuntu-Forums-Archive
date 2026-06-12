---
title: "powermizer"
date: 2008-06-27
forum: Hardware
---

### Post by ayu on 2008-06-27
Hi,
I was just playing around nvidia-settings (which seemed to have removed itself during the Hardy upgrade, but I never noticed it until now), and noticed something called PowerMizer. I've attached a screenshot. My card is a 8400m gs (laptop card). Is there any way to set the performance level to be lower? I don't need it on max all the time. 
Thanks!

---

### Post by sdennie on 2008-06-28
Unless you've done a PerfSrcLevel hack, it won't always be at maximum with that card.  If you have done a PerfSrcLevel hack with /etc/modprobe.d/options, revert it and use something like this: [http://ubuntuforums.org/showthread.php?t=828369](http://ubuntuforums.org/showthread.php?t=828369).

---

### Post by BForm on 2008-07-11
Are you using an external monitor? I'm using 64 bit Ubuntu 8.04 with a Nvidia 8400 M GS.  I think once twinview is enabled, it forces PowerMizer performance level 2. And *maybe*, (I haven't tested yet),  when I boot with an external monitor present it won't go back down from 2 even after it is unplugged, but if I plug in the monitor after ubuntu boots, then it will goto 2, but upon removal it goes back to being dynamic.

---

### Post by sdennie on 2008-07-11
> **BForm said:**
> I have the same issue. 64 bit Ubuntu 8.04, Nvidia 8400 M GS.  I think once twinview is enabled, it forces PowerMizer performance level 2. And it does not matter whether an external monitor is connected or not.  Googleing hasn't found me a fix yet...

Actually, I think you are probably right.  I hooked my machine up via HDMI to a TV the other day and noticed PowerMizer didn't drop after unhooking.  I believe I fixed it via nvidia-settings (and telling it I was only using 1 monitor).

---

### Post by ayu on 2008-09-01
No, I've never done the PerfSrcLevel hack. Yes, I usually have an external monitor connected, so I thought that might be it too. Then I tried booting up with nothing but AC power connected, and it still stays on maximum all the time. But at this point, I just hope the nvidia chip isn't faulty and completely burn out. Thanks anyways! :)

---

### Post by Chibone on 2008-09-02
There's an easy way to lower your clock ... Just add a line in your xorg.conf to enable dynamic clocking of your NVIDIA GPU (only with NVIDIA driver though).

Here's my card section in my xorg.conf (I use a Geforce 7000m):

```
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    # PowerMizer Levels
    # level 0×1 = highest
    # level 0×2 = med
    # level 0×3 = lowest
    # Dynamic   = PerfLevelSrc=0X3333
    Option	  "Coolbits"			"1"
    Option        "RegistryDwords" "PerfLevelSrc=0X3333"
    Option 	  "OnDemandVBlankInterrupts"	"true"
    Option        "RenderAccel" 		"true"
    Option        "AddARGBGLXVisuals" 		"true"
    Option        "NvAGP"			"1"
    Option	  "XAANoOffscreenPixmaps"	"true"
EndSection
```

The lines that probably of interest to you are:

```
    Option         "RegistryDwords" "PerfLevelSrc=0X3333"
    Option 	   "OnDemandVBlankInterrupts"	"true"

```

The PerfLevelSrc line enables the GPU clock to change on demand.   The OnDemandVBlankInterrupts saves power by cutting the number of times the card wakes up on idle (I think that's what it is, from what I read).  It enables a checkbox so you can always disable it through nvidia-settings if it does something funny.

My card used to stay at max performance all the time but now it downclocks to 100 MHz even while running Compiz.

You can also set it to be permanently lower by changing the value after PerfLevelSrc to 0x2 or 0x3 and it will stay there.  However, I prefer it dynamic so I don't suffer slowdown when I need the card at its best.

Screenshot of my nvidia-settings window after applying the xorg.conf settings: 

[ATTACH]83736[/ATTACH]

Down to 100 MHz! :)

Does this count as a PerfLevelSrc hack?

---

