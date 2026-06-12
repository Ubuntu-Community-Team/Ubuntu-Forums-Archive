---
title: "xrandr - can't find output at hex address that isn't even listed?"
date: 2018-10-15
forum: Hardware
---

### Post by dbsoundman on 2018-10-15
Hi all, this is a bit difficult to explain so hear me out.

I'm trying to use xrandr to create some scripts for swapping monitor configurations on a machine running Ubuntu 18.04 with i3 and i3-wm. The script looks like the following:
```
#!/bin/bash
EXTERNAL_OUTPUT="HDMI1"
INTERNAL_OUTPUT="LVDS1"

# if we don't have a file, start at zero
if [ ! -f "/tmp/monitor_mode.dat" ] ; then
  monitor_mode="all"

# otherwise read the value from the file
else
  monitor_mode=`cat /tmp/monitor_mode.dat`
fi

if [ $monitor_mode = "all" ]; then
        monitor_mode="EXTERNAL"
        xrandr --output $INTERNAL_OUTPUT --off --output $EXTERNAL_OUTPUT --auto
elif [ $monitor_mode = "EXTERNAL" ]; then
        monitor_mode="INTERNAL"
        xrandr --output $INTERNAL_OUTPUT --auto --output $EXTERNAL_OUTPUT --off
elif [ $monitor_mode = "INTERNAL" ]; then
        monitor_mode="CLONES"
        xrandr --output $INTERNAL_OUTPUT --auto --output $EXTERNAL_OUTPUT --auto --same-as $INTERNAL_OUTPUT
else
        monitor_mode="all"
        xrandr --output $INTERNAL_OUTPUT --auto --output $EXTERNAL_OUTPUT --auto --left-of $INTERNAL_OUTPUT
fi
echo "${monitor_mode}" > /tmp/monitor_mode.dat
```
Source: [https://faq.i3wm.org/question/5312/how-to-toggle-onoff-external-and-internal-monitors.1.html](https://faq.i3wm.org/question/5312/how-to-toggle-onoff-external-and-internal-monitors.1.html)

In my case, I ran 'xrandr' to get the appropriate names for $INTERNAL_OUTPUT and $EXTERNAL_OUTPUT, which turned out to be eDP-1 and DP-1-2, respectively. However, when I substitute these into the variables at the top of the script, xrandr always comes back with a really odd error:
```
xrandr: cannot find output 0x69
```

While I don't have the actual list of my display adapters handy with the corresponding hex addresses, I did search the output (even grepped it), and didn't find ANY device with that particular address, so I have no idea why it's trying to set that value in the first place. I also installed autorandr and ran into other issues that may be related.

The laptop in question is a Dell Dimension 5520, brand new. I'm wondering if there's some hokey dual graphics stuff going on that's preventing me from setting the display configurations. Any ideas?

Thanks!

---

