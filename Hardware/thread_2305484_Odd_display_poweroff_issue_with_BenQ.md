---
title: "Odd display poweroff issue with BenQ"
date: 2015-12-06
forum: Hardware
---

### Post by DigiAngel on 2015-12-06
So just got my new box setup (YAY)....got everything figured out but one thing...the display timeout and poweroff with the monitor.  Symptoms are the display goes to powersave (I'm assuming), the BenQ says "No signal detected", then I see the backlight come back on and I see the mouse cursor.  Here's what I see in syslog:

```
Dec  6 08:55:10 gamebox colord: device removed: xrandr-BenQ-BenQ GW2765-C9F00262019
Dec  6 08:55:11 gamebox colord: Automatic metadata add icc-102263e9c4e75c6b6d4259befc1ce500 to xrandr-BenQ-BenQ GW2765-C9F00262019
Dec  6 08:55:11 gamebox colord: Device added: xrandr-BenQ-BenQ GW2765-C9F00262019

```

Any hints on how to get this to actually work?  I even tried manually with the command line:  xset +dpms and xset dpms 120, but with the same results.  Thank you

---

### Post by matt_symes on 2015-12-06
Hi

Are you trying to turn off power saving on the monitor ?

If so then try this

```
xset -dpms
```

Kind regards

---

### Post by DigiAngel on 2015-12-06
Negative.  I'm wanting the monitor to go into poweroff/powersave mode after an idle timeout.  Thank you.

---

### Post by matt_symes on 2015-12-07
Hi

> **DigiAngel said:**
> Negative.  I'm wanting the monitor to go into poweroff/powersave mode after an idle timeout.  Thank you.

As a sanity check, does this command force the monitor off ?

```
xset dpms force off
```

Kind regards

---

### Post by DigiAngel on 2015-12-08
My first attempt was no....```
xset force dpms off
``` gave me a black screen, but it was not off...it was still backlit.  My second attempt actually worked though with:

```
xset +dpms
xset force dpms off
```

which is the first time I've seen it actually work.  The process has been:

BenQ goes black, compete with no backlitght
BenQ pops up a notification of "no signal detected"
BenQ backlight comes on and I see a mouse cursor

Using the two above step #3 didn't happen...it stayed off, so eh...I'm going to try two things...wait and see what happens after 5 minutes, and see what happens after rebooting.  Also, the only other change I've made since I started this thread is I plugged in a second monitor which is off.

Thanks for responding.

---

### Post by matt_symes on 2015-12-08
Hi

> **DigiAngel said:**
> 
```
xset +dpms
xset force dpms off
```

which is the first time I've seen it actually work.

That's good news

> , and see what happens after rebooting.

I don't think it'll survive a reboot.

Let's try another sanity test.

```
xset +dpms
xset dpms 0 0 120
```

Does that power off the monitor after 2 minutes ?

Kind regards

---

### Post by DigiAngel on 2015-12-08
Sooo....after suspend/sleeping the box, I get back and bam...no screen powerup.  I ssh'd into the box and tried everything, nothing so I sudo rebooted it.  At this point..meh...I' think I'll just live with it for now :)  Thanks again.

---

### Post by matt_symes on 2015-12-08
Hi

> **DigiAngel said:**
> Sooo....after suspend/sleeping the box, I get back and bam...no screen powerup.  I ssh'd into the box and tried everything, nothing so I sudo rebooted it.  At this point..meh...I' think I'll just live with it for now :)  Thanks again.

Odd. You may want to have a good look through ```
/var/log/Xorg.?.log*
```

Anyway, there's always the power button on the monitor I suppose :)

Kind regards

---

