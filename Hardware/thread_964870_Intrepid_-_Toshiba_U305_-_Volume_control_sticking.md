---
title: "Intrepid - Toshiba U305 - Volume control sticking"
date: 2008-10-31
forum: Hardware
---

### Post by jrf2027 on 2008-10-31
My Toshiba U305 has a volume control dial on the left side (you know, those weird things you spin with your thumb to raise or lower your volume).  The volume control dial works fine in Hardy - you adjust the volume, the volume level increases or decreases, the volume pop-up on the screen shows the volume increasing or decreasing incrementally, and then after the volume has been adjusted, the pop-up goes away.

Now, in Intrepid, whenever I adjust the volume, the volume pop-up on the screen shows the volume continuing to either increase or decrease after moving the dial even slightly - for instance, if the volume is low, and I move it just a little bit to raise the volume a slight bit, the bar in the pop-up shows the volume being pegged out at its max.  And it is indeed pegged out at its max!  Then, the volume pop-up continues to pop up every other second, probably because it thinks the volume knob is still being turned.  If I turn it the other way even slightly, the volume then goes all the way off, but once again the volume pop-up still appears every other second.

This happens in every possible configuration with Intrepid - happened with a clean install from the Live CD; happened with an upgrade from Hardy using the alternative install CD; it even happens when booting from the Live CD!  At the same time, the volume control works fine in Hardy as well as Windows XP and Windows Vista.

I assume that there is some sort of sensor on the volume dial that senses the direction and amount of movement of the volume dial, and that there is a driver for this sensor.  I also suspect that this driver is registering constant movement instead of incremental movement, and is not accurately returning information about the movement to the system.  However, my expertise ends at that point...anybody else have any ideas?

---

### Post by RiPPeR on 2008-10-31
I have a toshiba U300 and I am recieving the same error. 

As the OP stated Hardy was fine, but in ibex there seems to be a problem.

Hopefully this can be resolved soon.

Chris

---

### Post by metl_lord on 2008-10-31
I am having the same problem on my U-305. Hitting esc makes the popup go away, but then when I click on any icons, nothing happens. This forces me to restart. 

I hope this is a simple fix. That little dial is so convenient.

---

### Post by RiPPeR on 2008-10-31
> **metl_lord said:**
> I am having the same problem on my U-305. Hitting esc makes the popup go away, but then when I click on any icons, nothing happens. This forces me to restart. 

I hope this is a simple fix. That little dial is so convenient.

As a temp fix I mute the speakers (function + Esc for me) and it goes away for a while, also ctrl+alt+backspace restarts X so you dont need to do a full reboot everytime.

---

### Post by jrf2027 on 2008-10-31
I can't say that I'm "glad" that others are having the same problem...but at least I'm not alone.  

I'll be unable to assist in any troubleshooting this weekend, but come Monday, I can begin testing any proposed solutions.

---

### Post by ztrange on 2008-10-31
> **RiPPeR said:**
> As a temp fix I mute the speakers (function + Esc for me) and it goes away for a while, also ctrl+alt+backspace restarts X so you dont need to do a full reboot everytime.

I'm having the same issue, this is a confirmed bug on Intrepid due to the evdev driver, we need to wait until fixed.

The bug report is here, you may want to state that you are suffering the same issue...

[https://bugs.launchpad.net/fedora/+source/linux/+bug/271706](https://bugs.launchpad.net/fedora/+source/linux/+bug/271706) 

And you dont need to restart X, you may only need to go to a text mode session with ctrl + alt + f1 and back to X with ctrl + alt + f7. Just tested the fn + esc, but it works like esc it only puts out the big volume icon... 

By the way, and little off topic, do any of you who have an U300 or U305 managed to use bluetooth successfully? Are your laptops able to hibernate?

---

### Post by jrf2027 on 2008-10-31
> **ztrange said:**
> 

By the way, and little off topic, do any of you who have an U300 or U305 managed to use bluetooth successfully? Are your laptops able to hibernate?

Hibernate works for me under Hardy - haven't tried it out on Intrepid yet.  (I restored my Hardy image after getting frustrated with the volume control issue...)  I didn't do anything special.  It just seemed to work out of the box.  Mine's the U305-S2808, and doesn't have Bluetooth.

---

### Post by RiPPeR on 2008-11-01
Quick question jrf2027 - did you log a bug report for this?

If not I might go ahead an do so as I cant think of a solution.

Chris

---

### Post by RiPPeR on 2008-11-01
> **ztrange said:**
> By the way, and little off topic, do any of you who have an U300 or U305 managed to use bluetooth successfully? Are your laptops able to hibernate?

I have just tried the hibernate on 8.10 and it worked great! I've never tried to use bluetooth (although I do have it). Would be great to see it working 'out of the box' someday.

Chris

---

### Post by jrf2027 on 2008-11-01
> **RiPPeR said:**
> Quick question jrf2027 - did you log a bug report for this?

If not I might go ahead an do so as I cant think of a solution.

Chris

I didn't - because I thought it was already reported (see ztrange's earlier post).  Go ahead and do it, if you have the time.

---

### Post by jrf2027 on 2008-11-10
There is a workaround that solves the volume sticking issue...go to [http://ubuntuforums.org/showthread.php?t=974723]("http://ubuntuforums.org/showthread.php?t=974723") for the details.  Thanks again to ktemkin!

---

