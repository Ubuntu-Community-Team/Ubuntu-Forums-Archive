---
title: "HDMI connected LCD TV says &quot;No Signal&quot; After coming out of suspend/sleep mode"
date: 2013-08-24
forum: Hardware
---

### Post by john19 on 2013-08-24
Dear forum,
I currently have a Sony LCD TV to use as a desktop monitor along with Ubuntu 12.04 LTD, an ATI dedicated graphics card, and an AMD Phenom II processor. When I turn on the computer, everything is fine with the monitor, but after I leave it in suspend/sleep mode, and then get out of sleep mode by moving the mouse, the fan turns on and the computer goes out of sleep mode, but the monitor says "No Signal". I tried unplugging and replugging the HDMI cable from both sides, but all that disconnecting the cable does is it makes the Sony LCD TV say "Check signal cable". Lastly, I tried pressing "Alt + SysRq + " the five letters "R, E, I, S, U, B", and then the desktop resarted. 

Note that when I boot from a non-genuine version of Windows 7, the computer has successfully gone into and out of sleep mode while maintaining the signal to the monitor. Also, on a few occasions, I had Ubuntu LTS on suspend mode all night and in the morning the monitor worked fine.
 
I want to be able to consistently go into sleep mode without having to restart the desktop. One option I'm considering is buying a dedicated computer monitor that is not an hdmi-cable-commected LCD TV (hope that'll fix it right away). The other idea I'm currently considering is playing around with the graphics driver (sounds tricky) or just never using sleep mode again (boo).


Also, Adobe Flash hardware acceleration makes videos I stream turn glitchy and freezes up the whole computer, mouse and keyboard and all. Without hardware acceleration, I don't get the good HD picture that I *briefly* get with hardware acceleration. I'd like to be able to use hardware acceleration without the monitor freezing, although this is much less important of a feature than having sleep mode. If flash hardware support doesn't support Linux, it's no big deal.

So...Any ideas or solutions? Mostly regarding the first part about HDMI sleep mode signal issues?

---

### Post by john19 on 2013-08-24
Update: I tried using a DVI cable instead of an HDMI cable and the connection after coming out of sleep mode was still lost. My current solution is simply not using sleep mode anymore.

---

### Post by tophill24 on 2013-09-07
I've had similar problem using HDMI with an ASUS monitor: unable to resume after suspend.  I found that old kernel 3.5 works fine, while newer versions do not.  Haven't found how to fix, other than to keep and boot into old kernel.

---

### Post by andrea-gallo on 2013-11-21
> **tophill24 said:**
> I've had similar problem using HDMI with an ASUS monitor: unable to resume after suspend.  I found that old kernel 3.5 works fine, while newer versions do not.  Haven't found how to fix, other than to keep and boot into old kernel.

I have an ASUS UX32VD and I have been running 12.10 since beginning of 2013 and no issue with HDMI-DVI, not even after suspend. Yesterday after about three weeks of messages from the Ubuntu sw centre urging me to move to 13.04, I did it. What a mess.... whenever I get out of suspend, I just see a blinking blank cursor on my HDMI and my laptop display lights up with the same blinking "_" plus the mouse. I cannot do anything but force a power off.

In addition, the upgrade - should I say a downgrade - has removed all kernel headers and bumblebee does not work anymore. Need to find the right web page again :(

Where should I file the bug about the HDMI output after sleep? is it already filed on launchpad maybe?

thanks
AGallo

---

