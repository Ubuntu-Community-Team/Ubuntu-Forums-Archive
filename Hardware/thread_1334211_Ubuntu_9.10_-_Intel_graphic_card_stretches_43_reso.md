---
title: "Ubuntu 9.10 - Intel graphic card stretches 4:3 resolution to entire screen"
date: 2009-11-22
forum: Hardware
---

### Post by nemochin on 2009-11-22
Hello!

I was looking for a solution to my problem but failed to find any useful answer so I would like to ask here for a help.

I have a wide screen laptop with Intel graphic card. On Ubuntu 9.04 applications with a 4:3 native resolution in full screen mode had black borders on both sides of the screen. Now, in **Ubuntu 9.10**, they stretch to fill entire screen. **I would really like to have them embraced by those black borders to keep their original resolution.** It happens especially with games ran in Wine, but in my case using virtual desktop option in wine config is out of question since the game I care the most isn't working properly in virtual desktop. :(

I found some reversed cases when someone had those borders and want to get rid of them. Nevertheless I can't examine their settings because all of them were using **xorg.conf. In Ubuntu 9.10, as I can see, this file is no longer used.**

I'm not sure what additional data I should provide so I would really appreciate any help.

---

### Post by nemochin on 2009-11-23
**Update**

I've tried generating xorg.conf file who is not present in 9.10 by using "Xorg -configure" in terminal and placing this file in /etc/X11/ but it changed nothing. Then I added "Centermode", "NoStretch" and "LcdCenter" options and still nothing. The screen is still stretched! Is it really impossible to just order the screen to keep the 4:3 ratio instead of going to 16:10? :(

---

### Post by marwie on 2010-12-18
At the risk of bumping an old thread...

Looks like this is one more thing that's been moved from xorg.conf to xrandr. On my laptop I could fix it with this command:

xrandr --output LVDS1 --set 'scaling mode' 'Aspect'

After that, changing to a 4:3 resolution gives you black bars. You can add that line to your .xprofile so you don't have to type it again after reboot.

---

