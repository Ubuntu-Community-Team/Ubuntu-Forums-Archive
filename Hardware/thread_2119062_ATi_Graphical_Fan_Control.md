---
title: "ATi Graphical Fan Control"
date: 2013-02-22
forum: Hardware
---

### Post by nankura on 2013-02-22
hey guys

I was just wondering if theres a GUI tool to control your ATi fan speed, ive read up on a phew scripts, but im not that well versed in scripts

Like, when i was on windows ( i said a bad word sorry!!! ) i have a program called HIS iTurbo which comes with my HD 7770 graphics card, and it has auto overclocking and a fan control chart were i can set the speed > temp

I know nvidia have thermal control in linux with there drivers, but from what ive read is that ATi have no fan control which is extremely disappointing

---

### Post by QIII on 2013-02-22
In linux, ATI's Overdrive is terminal only.  On my cell phone right now, but will try to get back to this in a couple of hours.

My recommendation is not to modify fan settings.  You risk damage.

---

### Post by Yellow Pasque on 2013-02-22
@QIII: just tell the user to read
```
man amdconfig
```
and let him/her release the magic smoke. :popcorn:

Oh.. wait. I thought this was the Gentoo forum. Nvm..

---

### Post by QIII on 2013-02-23
Well, the reason I recommend against changing the fan speed manually is because of that magic smoke!

@nankura

I strongly recommend* against* manually controlling fan speed.  AMD/ATI made the card to take care of itself.  If you set the fan speed too low, you could find yourself setting off your smoke alarm and taking an unexpected trip to the computer parts store.

That said, the magic forumula is:

```
amdconfig --pplib-cmd "set fanspeed <id> <percent>"
```Where id is the fan ID (0 based, so 0  if you only have one card) and percent is the percent of max fan speed you want.

For example, to set the fan to 40% speed:

```
amdconfig --pplib-cmd "set fanspeed 0 40"
```To get it back to auto control:

```
amdconfig --pplib-cmd "set fanspeed 0 auto"
```Be aware that some users report that going back to auto does not take effect until reboot.

---

