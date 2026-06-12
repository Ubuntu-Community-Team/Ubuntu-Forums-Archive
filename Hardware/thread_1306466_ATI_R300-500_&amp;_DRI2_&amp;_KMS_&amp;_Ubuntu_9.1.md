---
title: "ATI R300-500 &amp; DRI2 &amp; KMS &amp; Ubuntu 9.10"
date: 2009-10-30
forum: Hardware
---

### Post by restart on 2009-10-30
Ok, I have ATI Mobility Radeon X1600 (R5xx chip).

I just activated KMS (so DRI2 activated too) by adding
```
radeon.modeset=1
```
to GRUB loader.

Results:
+ compiz finally works without artifacts. For example, moving windows with OpenGL now doesn't let "OpenGL part" of window stay in the old position while window's edge already on the new position.
+ tty1-6 finally got the native display resolution (there was very low resolution without KMS & DRI2 in Jaunty, and there was absolutly awful "pixel chaos" when trying to switch to console tty1-6 on Karmic).

and minuses
- the total performance become a bit lower. Gears give lesser fps (who cares about gears), and 3D applications become a bit slower too.
- the main minus for me: compiz (yes, it works without any glitches) become slow! Minimizing/restoring windows is laggy, "CUBE" is laggy and so on.

So the questions is:
what are the further "tuning" tips? I like the result in general case, but partially performance become worse.
To DRI2 or not to DRI2? :)

---

### Post by restart on 2009-10-31
anyone?

---

### Post by Melf on 2009-10-31
I can pretty much report the same behaviour.
If you wan to experiment, you can try the x-org-edgers
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
or perhaps a new kernel (2.6.32).

Right now i am using the x-org-edgers ppa and the stock karmic kernell and at least the meaningless fps count in glxgears seems to be a bit higher :D

BTW, at least in my case (x2300(RV535)@asus f3jr laptop) suspend with KMS is broken. The laptop just does not go to the low power mode after suspending, the fan is running and it does not respond to anything.
On the other hand, hibernation works without problems :)

---

### Post by restart on 2009-11-04
> **Melf said:**
> I can pretty much report the same behaviour.
If you wan to experiment, you can try the x-org-edgers
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
or perhaps a new kernel (2.6.32).

Right now i am using the x-org-edgers ppa and the stock karmic kernell and at least the meaningless fps count in glxgears seems to be a bit higher :D

BTW, at least in my case (x2300(RV535)@asus f3jr laptop) suspend with KMS is broken. The laptop just does not go to the low power mode after suspending, the fan is running and it does not respond to anything.
On the other hand, hibernation works without problems :)

Thank you very much for answer. Even google can't advice anything about it :)
I didn't try suspend (my laptop has battary broken so it helpless for me to suspend it :) ), but hibernation works well for me too.
How much is the chance of the new kernel, mesa and drivers versions will be added in official karmic repos? And when do you think this will happen?

---

