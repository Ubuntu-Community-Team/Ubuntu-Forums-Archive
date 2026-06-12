---
title: "Extended mon itor doesn't get the correct resolution"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by lsepulve on 2007-10-19
Hi there,
I have bought a new Viewsonic (VA1903wb 19" lcd), and I put this as an extended monitor for my dell computer. the problem is that I can't get the best rosolution (1440x900), it only give me 1280x1024, so I see everything very fat.

I tried the new "Monitors & Graphic" tool, but since the exact model is not available, I choose a generic LCD monitor with the resolution 1440x900, but when I set that and reboot, the X system can't start.. so I have to get back to my old xorg.conf file.

Waiting for your comments,

Luis

---

### Post by loveshackdave on 2007-10-19
"In Theory" adding the following Subsection to the Screen section of your xorg.conf should enable 1440x900, though I have the same problem and haven't ever been able to get it to work. I finally was able to get 1280x800 to work by playing around with different monitors. Good luck, and if you figure it out, let us know.

Section "Screen"
....
SubSection "Display"
Depth 24
Modes "1440x900"
EndSubSection
....
End Section

Section "Monitor"
....
Modeline "1440x900@60" 108.84 1440 1472 1880 1912 900 918 927 946
....
EndSection

---

### Post by lsepulve on 2007-10-19
Hello again.. 
I tried what you suggested, but nothing happened, the resolution is still 1280x1024, and it doesn't show me the 1440x900 I want.

Thanks anyway, is good to know that there is always someone who wan to help.

I hope somebody else has the solution though.

Greetings!!

---

### Post by lebihan1 on 2007-10-19
both my monitors are set to 1440x900, if you have an nvidia graphics card, adding the following options in your xorg.conf might work... this is what worked for my laptop with an external monitor...

#Twinview Setup

Option          "TwinView" "true"
Option          "MetaModes" "1440x900,1440x900"
Option          "TwinViewOrientation" "LeftOf"

the last option is which side your external monitor resides on, but if both monitors aren't 1440x900, you will probably have to dig deeper into the forums to find the fix... hope this helps :)

---

