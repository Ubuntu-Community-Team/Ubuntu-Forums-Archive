---
title: "Suspend, hibernate and suspend-hybrid (Asus T91, 11.04)"
date: 2011-07-09
forum: Hardware
---

### Post by onebir on 2011-07-09
My question is: how to set up the "power button" so that it has a suspend-hybrid option?

Below is some background:

It looks like all suspend, hibernate and suspend-hybrid all work fine out of the box (congratulations, Ubuntu people!). I used (a) *sudo pm-suspend-hybrid* to test the latter, and the menu choices for (b) suspend and (c) hibernate. The relevant lines in /var/logs ended:
a) *... /usr/lib/pm-utils/sleep.d/000kernel-change **suspend suspend_hybrid**: success.* 
b) ... */usr/lib/pm-utils/sleep.d/000kernel-change **suspend suspend**: success.*
and
c) */usr/lib/pm-utils/sleep.d/000kernel-change **hibernate hibernate**: success.*

For a netbook with an SSD, "suspend_hybrid"  has seems like a good option (quicker resume, and but like hibernate no risk of problems if the battery runs down.)

I looked in gconf-editor at /apps/gnome-power-manager/buttons/suspend. The value was "suspend". "suspend" and "hibernate" appeared in the log file as well as being listed as possible values. So I thought the value might just contain the name of a script, and given that "suspend_hybrid" appeared to work from the CLI, tried changing the value to "suspend_hybrid".

But it doesn't seem to work; pm-suspend.log just says:
```
Activating Runtime PM for device type i2c
```I don't know where to go from here.

(But at least I've discovered gconf-editor ;) )

---

### Post by themadhatter0 on 2011-07-25
I tried to fix suspend-hybrid a while ago too and had similar difficulties. There is a utility to check if suspend-hybrid is supported called pm-is-supported. Try running:

```
pm-is-supported  --suspend-hybrid && echo Yes
```

It is supposed to echo "Yes" to the command line if suspend-hybrid is enabled, but it only works if I run it as root (or using sudo), whereas it returns "Yes" when I run it as me with the --suspend or --hibernate options. I tracked this problem down to the file /usr/lib/pm-utils (which contains the bash script that's executed when you run pm-is-supported). On line 347 you'll see:

```
if [ -z "$SUSPEND_HYBRID_MODULE" -a -w "$PM_RTC/wakealarm" ] && 
blah blah blah
```

This is testing that $PM_RTC/wakealarm exists and is writable - $PM_RTC is defined at the top of the file as /sys/class/rtc/rtc0, which is only writable by root!

I suspect this is a clue as to why suspend-hybrid is not working properly. I guess it has to work for your user, not just root, otherwise you would need to type in your password every time you want to put your machine to sleep!

I think I'm close - hopefully someone else can put the final pieces of the puzzle together!

---

### Post by themadhatter0 on 2011-08-01
It's not an ideal solution to your problem, but the following steps will force suspend-hybrid for all powersave actions (i.e. when you push the power button, when you close the laptop lid, after the powersave timeout). It's the best solution I have come up with so far, and it's probably acceptable in most cases:

```

sudo gedit /usr/lib/pm-utils/bin/pm-action

```

Near the top of the file, change:

```

export METHOD="$(echo ${0##*pm-} |tr - _)"

```

to:

```

#export METHOD="$(echo ${0##*pm-} |tr - _)"
export METHOD=suspend_hybrid

```

Cheers,
Scott

---

