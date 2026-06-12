---
title: "Disable touchpad (but not stick) on Dell Latitude D820?"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by fargle on 2006-06-06
I always see tons of posts asking how to enable/disable tap-to-click, scrolling, you name it, but here's kind of the opposite question:

I have a Dell Latitude D820 (nice, killer battery life and works great with Dapper, by the way, except there are some suspend issues I need to work on) which has an ALPS DualPoint built in.  That's the one that has both a pointer stick and a touchpad.

I know this may sound like heresy to some of you, but I HATE touchpads.  They take up too much real estate on the keyboard and I'm constantly bumping them with my thumbs causing the pointer to skate all over.  In contrast, I love the stickpointer, especially this new one with a nice nubby cover on it.

So the question is, has anyone seen how to disable the touchpad while leaving the stickpointer active?  I've searched high and low and can't find anything.  There are some comments in the Synaptics driver that seem to be talking about bitmasks on the packets coming in that allow for differentiation of the two, but also say "We'll just OR them together for now", so I may have to get my hands dirty and try some coding to add an option to the driver, but first I was wondering if anyone knew of anything easier.

---

### Post by Patsoe on 2006-06-10
Aren't the touchpad and the trackpoint two separate devices in /etc/X11/xorg.conf? If not, then I wouldn't really know a trick just now.

BTW, I hate touchpads too!! Just couldn't afford a machine with a trackpoint... like a Dell Latitude or a Thinkpad... so I'm stuck with a touchpad only.

---

### Post by savastux on 2006-06-20
So do I!
 
I really don't like it, especialy when I'm typing a text and my wrist accidentally touches on it.:mad: 
 
So I disable it.
 
The way I've managed to disable only the touchpad is just like Patsoe said: Disable via xorg.conf
Accupoint and Touchpad have diferent configurations, so let's do it...
 
Here is my xorg.conf segment. If you are using a D820, I think yours should be equal or very similar. BTW I don't have the fingerprint reader on my touchpad.
 
```

 
Section "InputDevice"
            Identifier               "Synaptics Touchpad"
            Driver                   "synaptics"
            Option                   "SendCoreEvents"       **"true"**
            Option                   "Device"               "/dev/psaux"
            Option                   "Protocol"             "auto-dev"
            Option                   "HorizScrollDelta"     "0"
            Option                   "SHMConfig"            "1"
EndSection
 

```
 
You only need to change the "true" (in "SendCoreEvents") to **"false"**.
Restart X. 
 
And there you go... Accupoint on and touchpad off.
 
Before I did this, I've tried to use qsynaptics (thats the reason there is a SHMConfig Option in my xorg.conf) but for some reason the configuration just doesn't stick.
 
Hope this work out for you.O:) 
Bye.

---

### Post by menaar on 2006-06-22
I know what you mean.

I have been using qsynaptics for some time, to turn off the touchpad, because I hate the touchpad It always gets in my way.

But it never sticks, and when i reboot, I've got to go disable again.

I will try your suggestion.

I'll let you know if it worked,

---

### Post by menaar on 2006-06-26
Thanks for the suggestion to change the "true" to "false"

I hope this will help people who are struggling through all these programs qsynaptics, gsynaptics, etc....

Whoever just doesn't want to use the touchpad, follow the advice given here.

Just change the value from "true" to "false" in the xorg.conf.

---

### Post by tsukurite on 2006-12-11
> **menaar said:**
> Thanks for the suggestion to change the "true" to "false"

I hope this will help people who are struggling through all these programs qsynaptics, gsynaptics, etc....

Whoever just doesn't want to use the touchpad, follow the advice given here.

Just change the value from "true" to "false" in the xorg.conf.

I just posted here: 
[http://www.ubuntuforums.com/showpost.php?p=1873855&postcount=13]("http://www.ubuntuforums.com/showpost.php?p=1873855&postcount=13")
regarding my setup in a d820.  With the synaptics driver installed you can use the shell script I've attached in the post to enable/disable the touchpad.

Regards.

---

