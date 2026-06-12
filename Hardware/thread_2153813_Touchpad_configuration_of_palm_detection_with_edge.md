---
title: "Touchpad configuration of palm detection with edge palm detection"
date: 2013-06-12
forum: Hardware
---

### Post by noisygecko on 2013-06-12
I have an ASUS UX32A and am running Ubuntu 13.04.  I have configured palm detection manually using xinput and a startup script and it works.  But, the touchpad keeps detecting my palm at the edge of the touchpad as a small areas and treats it as a touch event.  Does anyone know how to tweak the settings to fix this?  I have disable while typing going, but if I pause my typing I get touch events periodically.

I know a bit about this having had to hack my way into getting things halfway working -- even these days I am amazed how hard this is to get going.  I am using a startup script to run 'xinput' to turn on palm detection and have changed the values to work for detecting palms in the center of the touchpad.  My current palm detection parameters are (4 is the smallest I can make it to still detect my finger):

[INDENT]Synaptics Palm Detection (287): 1
Synaptics Palm Dimensions (287):     4, 1
[/INDENT]

But I finally have turned off touch to click because my palm keeps getting detected at the edge of the touchpad.  Are there 'xinput' parameters that I can change to avoid those edge clicks?

Is there a tool to display the touch events that are occurring?  I am looking for something like 'xev', but for touchpad events.  I would like to be able to see what is being detected to tweak the 'xinput' parameters.  It needs to display multitouch events, size, etc.

This problem really needs to be solved.  MacBooks have been doing this for years, and even Windows does this (I guess).  They all have tweaked lots of these parameters to make large touch pads usable.

---

### Post by noisygecko on 2013-06-12
I guess I figured out a solution.  I am very surprised that I never have seen anyone post anything about this.

It turns out there is another 'xinput' parameter that can turn off touch events on the sides.  I had tried the "Synaptics Edge" parameters, but that only seems to work for edge scrolling, so it wasn't changing anything.  I never noticed the "Synaptics Area" parameters.

So, here is what I have in a script that is run when I log in that is tailored for the touchpad on my ASUS UX32A:

```
##!/bin/bash
#
# File: .ubuntu_touchpad_settings.sh
#
# Change settings to do palm detection and disable touchpad while
# typing.  Make sure that "Disable while typing" is turned off in
# "Settings", "Mouse & Touchpad".
#
# Add this to startup scripts:
#
#   Dash "startup settings"
#   Add startup entry:
#
#     bash /home/user/.ubuntu_touchpad_settings.sh
#

# Touchpad device.  Use 'xinput' to find the name.
# To view property values:  xinput list-props "$TOUCHPAD"
TOUCHPAD="ETPS/2 Elantech Touchpad"

# Turn on palm detection for anything larger that "4".
xinput set-prop "$TOUCHPAD" "Synaptics Palm Detection" 1
xinput set-prop "$TOUCHPAD" "Synaptics Palm Dimensions" 4 1
# Ignore touch events on the left and right edges since palm detection doesn't work there.
# Using the same X values as the "Synaptics Edges" parameter.
xinput set-prop "$TOUCHPAD" "Synaptics Area" 130 3130 0 0

# Now change the settings for disabling touchpad while typing.
syndaemon -i 1.0 -K -R -d
```

I guess I'll try this out a bit before I mark it solved.  Disabling the edges doesn't seem to be very noticeable when using my finger, but appears to stop all palm touches on the edges.  The values I used for the "Synaptics Area" are the same X values that were the defaults for the "Synaptics Edges" parameter.

---

### Post by wb8nbs on 2014-04-28
This is working for me on an N56VJ. I added
 synclient AreaBottomEdge=1825
to the end of the script to keep the cursor steady while pressing the mouse buttons.

Also note, two finger scrolling now requires the fingers to be farther apart or palm detect kicks in.

---

