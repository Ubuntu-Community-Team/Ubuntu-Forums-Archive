---
title: "PC pretty much dead after downloading all night"
date: 2012-07-25
forum: Hardware
---

### Post by sofasurfer on 2012-07-25
I was downloading a bunch of audio tracks using "clipgrab". Had lots of time left so I went to bed and let it run. This morning PC was in sleep mode. I hit keyboard to wake it up and nothing happened. 
I have to unplug to shut down. Then I hit the start button and the monitor comes to life but goes directly to power saving mode.

Power off switch ---- inoperative
reset switch --- inoperative
monitor --- stays in energy saving mode
DVD player --- has light on but no motor spinning
hard drives --- not spinning
case fan --- runs
power on switch --- on
temp display --- on, until the last time I restarted pc, now it is not on

Is this a dead power supply? Motherboard? CPU?

---

### Post by Easy Limits on 2012-07-25
If your power supply was toast none of the other devices would turn on.

---

### Post by jmfal on 2012-07-25
Check that the psu  is set to right current  110/220

---

### Post by ahallubuntu on 2012-07-25
> **Easy Limits said:**
> If your power supply was toast none of the other devices would turn on.

Not true.  I have had bad power supplies more than once that would still provide enough power for the fans but not enough to POST the motherboard.  Power supplies don't have to fail all-or-nothing.  They can lose part of their ability to supply power.

In this case, it's easier to swap in another power supply to see if that fixes it.  The average person does not have a power supply tester handy, unfortunately, though even a power supply tester might not show it to be completely bad.

If another (probably good) power supply does the same thing, then I'd unplug all the unnecessary components (unplug all drives and cards, everything but the keyboard, one stick of RAM and the video card unless there's integrated video, then unplug an added video card as well) and try again.  Try again with the other stick of RAM.  Try again with one stick in another RAM slot.  Any change of behavior?
 
You can also try clearing CMOS settings.  Sometimes there's a jumper on the motherboard to do that; if not, you can unplug all power and remove the little CMOS battery for about a minute, then plug it back in, try again.

At this point of testing everything above: if there is no integrated video, then the dedicated video card COULD be bad.  Or the motherboard probably is.  Fact of life, motherboards fail.  In my experience, a power supply failure is more likely than motherboard failure, though.  Especially if it's a no-name power supply.  I've replaced lots of them.

---

