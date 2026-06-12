---
title: "Tuning Synaptics Tap To Click"
date: 2007-11-21
forum: Hardware &amp; Laptops
---

### Post by csete on 2007-11-21
Hello,

I have a Dell Inspiron E1505 laptop that I've recently started running Gutsy on dual-booted with Windows Vista.  I'm slowly getting things configured to my liking, but one thing I can't seem to get set up is the Synaptics click-to-tap settings.  Movement and edge movement work great.  But, I can't seem to get click-to-tap to work the way things seemed to work in Windows.  It *seems* to be related to the way that I use my index finger.  If I press with the very tip of my finger, it seems to work much better than the way I normally use the pad of my finger.

I've been using synclient to try to find some combination of parameters that work better, but I'm really having no luck.  Can anyone offer any insights into good parameters for this laptop?

Thanks,
Craig

---

### Post by spier on 2007-11-21
Hi, Craig, it is my though that there is no default toutchpad config. It is a matter of hardware and body combination. Something that works for my tick fingers wil confuse others, eventually. 

Thisl said, you should tune your hardware the way you fill more comfortable through touchpad's settings in   /etc/X11/xorg.conf. You can change tap behaviour playing with MaxTapTime, MaxTapMove, FingerLow, FingerHigh. 
A good explanationf for each option you'll find [here]("http://linux.die.net/man/5/synaptics")and [an example here]("http://ubuntuforums.org/showthread.php?t=168581&page=3").

HTH,

---

### Post by csete on 2008-01-29
I'm continue to be very frustrated with my  tap-to-click settings in Gutsy.  I've tried everything I can think.  I've played with synclient monitoring and changing parameters using synclient.  I cannot seem to find a combination of parameters that feels comfortable and is sensitive enough.  The click to tap works sometime just fine and then the next click I have to whack really hard to get a click.  After spending a lot of time trying to get this to work, it seems like the things that help me get a successful tap to click... I can hit the pad really hard or I can hit it softly with the very tip of of my finger.  It seems to be somewhat related to the size of the surface of my finger that I hit the touchpad with.  Does that make sense?  I've tried disabling palm detect thinking it might be triggering, but that didn't help either.  Everything else (edge scrolling, etc.) seems to work quite well... it is just tap-to-click.

I really want tap-to-click to work as well as on Windows.  It is something I've used for years and I don't really want to retrain myself to have to use the associated mouse button.  I'm surviving in Linux, but getting more and more frustrated that I can't get this tuned up correctly.

Please help.
Thanks,
Craig

---

### Post by kegobeer on 2008-01-29
Would you post your xorg.conf file?

---

### Post by csete on 2008-01-29
Do you want the whole file or just the Synaptics configuration?  Here is the synaptics section and I can also post the whole file if it is helpful.

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"SHMConfig"		"on"
#        Option          "LockedDrags"   "1"
        Option          "FingerLow"     "3"
        Option          "FingerHigh"    "20"
        Option          "MaxTapTime"    "180"
        Option          "MaxDoubleTapTime"      "180"
        Option          "MaxTapMove"    "110"
#        Option          "VertScrollDelta"       "20"
#        Option          "HorizScrollDelta"      "20"
#        Option          "MinSpeed"      "0.10"
#        Option          "MaxSpeed"      "0.50"
#        Option          "AccelFactor"   "0.005"
#        Option          "EdgeMotionMinSpeed"    "200"
#        Option          "EdgeMotionMaxSpeed"    "200"
EndSection

```

As you can see, I've been trying lots of different things trying to get this going.  I've also tried a lot of combinations via synclient that aren't shown here.

Thanks,
Craig

---

### Post by csete on 2008-01-30
Bump

---

