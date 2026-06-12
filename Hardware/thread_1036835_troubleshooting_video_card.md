---
title: "troubleshooting video card"
date: 2009-01-11
forum: Hardware
---

### Post by wmdiem on 2009-01-11
Hi all. Quick noob question:
I suspect something is wrong with my video card (3d games have crazy lag, some video playback is broken, i.e., pauses). 

lshw shows display 0 and display 1 (Mobile GM965/GL960 Integrated Graphics Controller) as unclaimed. 


/etc/X11/xorg.conf also has nothing under the entries for "Configured Video Device" and "Configured Monitor"

I am wondering whether I screwed something up when I uninstalled Jockey (in order to use a MadWifi). 
I know nothing about video cards, so even some basic diagnostic help would be really appreciated.
I'm running 2.6.24-21-generic, 8.04.
Thanks

---

### Post by mikewhatever on 2009-01-11
I am not sure about 3d games, but Intel graphics accelerators aren't really made for them. You may want to try checking if the **xserver-xorg-video-intel** package is installed. In addition, what are your specs, CPU, RAM.

---

### Post by wmdiem on 2009-01-11
The package is installed. 
It's pretty low end: 1.7Ghz and 1GB, but the game I was testing din't *seem* very demanding (it was a 3d platform strategy game, not a demanding flight simulator or FPS) but the lag was just incredible. Also, intuitively I am feeling that playing a DVD should never have hesitation on a computer that came out in the last couple years, even on a commodity laptop (unless some process kicks in, but the hesitation is always in the classic high-replacement scenes, explosions and such).

Edit: The reason I suspect there is some driver or configuration issue is that I didn't notice problems under Vista (which is what came on the computer). Even with Vista's bloat, I was able to play AoE with no problem (until there was a massive battle, in which case I had to turn down the resolution to keep the lag down).

---

### Post by mikewhatever on 2009-01-11
What games do you play under Linux? Is it AOE? Is it another game you run on wine? The big difference is that AOE is made for Windows and can't run natively on Linux.

> Also, intuitively I am feeling that playing a DVD should never have hesitation on a computer that came out in the last couple years...

Was that an instance of wishful thinking?

Try checking how much RAM is allocated for the graphics in the BIOS settings. Chances are you may increase the amount and thus gain in performance.

---

### Post by wmdiem on 2009-01-11
it was a native linux game (installed via synaptic), i'm sorry to say i don't remember the title: i deleted it about a week ago because it was unplayable (I've been checking and it looks like it was Warzone 2100). 
And perhaps it was wishful thinking, I'm guess i'm blow away that a full-out computer with over a gig processor and a gig of RAM can't handle what a $25 dedicated pos dvd player can. 
I will check the bios settings, but is it normal to have the video card unclaimed? Like I said, i don't know anything about video cards, and I don't know much about how linux controls hw in general, but is it possible i'm falling back into some sort of legacy/generic video mode, and thus forcing the main processor and system memory to handle all of the graphics processing directly?

---

### Post by wmdiem on 2009-01-11
I found this: [http://hardware4linux.info/component/28740/](http://hardware4linux.info/component/28740/)
Someone has posted the xorg.conf he is using for this video card. 
And i notice that it has a number of settings defined that aren't in mine (since mine is basically blank, concerning the video device). Specifically I note the following entries:

```
Section &#8220;Module&#8221;
Load &#8220;i2c&#8221;
Load &#8220;bitmap&#8221;
Load &#8220;dbe&#8221;
Load &#8220;extmod&#8221;
Load &#8220;type1&#8221;
Load &#8220;freetype&#8221;
Load &#8220;glx&#8221;
Load &#8220;vbe&#8221;
Load &#8220;dri&#8221;
EndSection
```

and

```

Section &#8220;Device&#8221;
Identifier &#8220;Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller&#8221;
Driver &#8220;intel&#8221;
BusID &#8220;PCI:0:2:0&#8221;
Option &#8220;DRI&#8221; &#8220;true&#8221;
Option &#8220;XVideo&#8221; &#8220;true&#8221;
#Option &#8220;DisplayInfo&#8221; &#8220;true&#8221;
Option &#8220;RenderAccel&#8221; &#8220;true&#8221;
Option &#8220;XAANoOffscreenPixmaps&#8221; &#8220;true&#8221;
#Option &#8220;AccelMethod&#8221; &#8220;EXA&#8221;
EndSection

```

Now I'm wondering whether I ought to add these to my xorg.conf or will they just screw up X11? 
Any ideas? Does this looks safe and make sense?
thanks for your help

---

### Post by mikewhatever on 2009-01-12
The fact of having an unclaimed device is odd. Can you post the output of <sudo lshw -C display>.
I don't have an Intel graphics card, and so can't tell how well they perform, but it would be a shame if Intel graphics had a lousy Linux support.
About the xorg options, the guide is rather old, and ever since Hardy, xorg.conf has more comment lines then configs. Try it if you want, just backup the original file, <sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-original>

---

### Post by wmdiem on 2009-01-13
```

 sudo lshw -C display
[sudo] password for wmdiem: 
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0

```

---

### Post by mikewhatever on 2009-01-14
Hm..., are there two?

---

### Post by wmdiem on 2009-01-14
Theres the laptop monitor, the S-video, and the regular monitor jack. I don't know what card(s) is inside or how it is recognized. It is a laptop and I was assuming it was integrated, but i've never looked inside.

---

### Post by mikewhatever on 2009-01-15
Right, I obviously didn't expect you to take it apart, just asked to get it out of the way. I've done some searching, and it appears that Mobile GM965/GL960 Integrated Graphics Controller doesn't supports 3d. Hope I'm wrong though.
[http://ubuntuforums.org/showthread.php?t=709672](http://ubuntuforums.org/showthread.php?t=709672)
[http://ubuntuforums.org/showthread.php?t=974436](http://ubuntuforums.org/showthread.php?t=974436)

---

### Post by wmdiem on 2009-02-05
I fixed it. I just made sure libgl1-mesa-glx and libgl1-mesa-dri were installed. Now openarena works great.
This is the link where I figured out what was going on: [http://forum.compiz-fusion.org/showthread.php?p=57769](http://forum.compiz-fusion.org/showthread.php?p=57769)

---

