---
title: "Double tap to turn off touchpad"
date: 2010-09-17
forum: Hardware
---

### Post by gpenguin on 2010-09-17
I have an HP Mini 210-1142CL and Netbook Remix installed fine and almost everything is working great.  However, I read in the paperwork with the system double-tapping in the upper-left corner to "turn off" the touch pad so while typing, accidentally touching the touchpad didn't send the cursor all over the place.

Anyone know how to get this working or something similar?  It would be nice to time, rest my hands, and not worry about the touchpad bouncing my cursor around.  When done typing, re-enable the touchpad and go about my day.

Thanks!

--GPenguin

---

### Post by sGroggy on 2010-09-17
I have the same issue with my HP DV3-4000sb, double tapping in the upper left corner of the touchpad does not turn it on/off like it should.

I have not tried this myself, but you could try the following option from the synaptics driver:

```
Option "PalmDetect" "boolean"
              If  palm  detection  should  be  enabled.   Note  that this also
              requires hardware/firmware support from the touchpad.  Property:
              "Synaptics Palm Detection"

```

If you just want to turn it off you can do 'synclient TouchpadOff=1'. To turn it back on just do 'synclient TouchpadOff=0'. To list all settings you can do 'synclient -l'. I'm not sure if synclient is installed by default or not, if not, just install it of course... :)

Greetings

---

### Post by gpenguin on 2010-09-24
> **sGroggy said:**
> I have the same issue with my HP DV3-4000sb, double tapping in the upper left corner of the touchpad does not turn it on/off like it should.

I have not tried this myself, but you could try the following option from the synaptics driver:

```
Option "PalmDetect" "boolean"
              If  palm  detection  should  be  enabled.   Note  that this also
              requires hardware/firmware support from the touchpad.  Property:
              "Synaptics Palm Detection"

```

If you just want to turn it off you can do 'synclient TouchpadOff=1'. To turn it back on just do 'synclient TouchpadOff=0'. To list all settings you can do 'synclient -l'. I'm not sure if synclient is installed by default or not, if not, just install it of course... :)

Greetings

synclient doesn't seem reliable.  I had to issue TouchpadOff=1 twice in order for it to take and sometimes moving the mouse would "re-enable" it.  Anyone know if the desktop manager is re-enabling it on its own?  I'm trying to use it now and it stops for a bit and then re-engages.

Thoughts?  Wait...just had a thought...hold on...Hmmm, let's see...WORKING!!!!

I had "Disable Touchpad while Typing" set in my mouse settings.  As a result, the window manager was monitoring my typing.  When I stopped typing *IT* would re-enable the touchpad.  If I uncheck that option, the above synclient commands work great.  In fact, mapping them to hotkeys, I can enable and disable the touch pad quickly and easily and do some serious typing without worry.

Thanks guys!!!!

--C64Whiz

---

