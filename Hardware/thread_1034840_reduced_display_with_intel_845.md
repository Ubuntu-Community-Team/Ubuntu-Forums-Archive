---
title: "reduced display with intel 845"
date: 2009-01-09
forum: Hardware
---

### Post by yayou on 2009-01-09
Hi everybody

First of all I have to warn you that I’m from a French speaking country, so don’t be too rigorous with me about some strange mistakes I could make. 

I have a problem with ubuntu since 8th version. With the 7th everything was right. When I’ve installed the 8th version I obtained a reduced display. My physic screen  dimension is 14 inches but with ubuntu I clearly have less than that, perhaps 10 inches. My graphic card is an intel 845. I followed instruction to solve incompatibility problems according to my configuration, but it failed. I tried to downgrade to 7th version but I had an installation problem; in fact I wanted to install the 7th version and update it to have 8th version. But the installation problem didn’t allow me doing this. Could you please help me?

---

### Post by niceguy123 on 2009-01-09
Hi,

I'd like help with the opposite, I'm running a Sony vaio 16.4 screen aspect ratio 16:9. the resolution is now set at 800X600 4:3 and the result is that it everything is a little stretched out of proportion. In Ubuntu's resolution manager there are only two options. Is there a way to configure this via terminal?

---

### Post by yayou on 2009-01-17
Is it possible that those problems had already been resolved?

---

### Post by blazerw on 2009-01-18
I've just spent a lot of time messing with my laptop with the intel 845. I got it working using the "intel" driver and adding one of these options to the /etc/X11/xorg.conf file in the "Device" section.
First, this is sorta the failsafe option:
Option "NoAccel" "true"

The above produces a sluggish X desktop, though. If the above worked, remove it (remark it out with a "#" in front), and try this one:
Option "DRI" "false"

The above DRI option works nicely, but if it doesn't work you can also try:
Option "EXANoComposite" "true"

Now, after all that let me point out that I did not have your problem. My X locked up on startup. So, I'm suspecting you might be using the "i810" driver instead of the "intel" driver. Look in the "Device" section for driver and make sure it is "intel".

If it is Intel, the most likely cause of your low resolution is that X is not detecting your monitor correctly. You can try System->Preferences->Screen Resolution and click the Detect Displays. However, I wouldn't expect that to work any better. So, you might have to look up how to enter your display information into the xorg.conf file in the "Monitor" section.

A lot, I know, but I hope it helps.
-Randy

---

