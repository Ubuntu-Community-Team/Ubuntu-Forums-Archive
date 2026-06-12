---
title: "Fn HotKeys"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by Seeker84 on 2007-06-04
Alright so I've read that the Fn keys make function calls to make everything work.  I have a dell Inspiron 700m and as many of us know that WiFi works but the LED doesn't toggle on and off.  one solution is to edit the LED file and make it always on.  As pleasant as this sounds, I'd rather code into the function call and have the hotkey toggle the LED on and off.  I tried to use showkey, dumpkeys, but to I keep getting the "Couldnt get a file descriptor referring to the console" message  I can see some file that looks promising in /usr/share/hotkey-setup/dell.hk.  but with out seeing what keys lie where I don't want to use setkeycodes just yet.  If anyone has successfully created hotkeys using the Fn button please, any advice would be helpful.

---

### Post by Seeker84 on 2007-06-07
I'm still here waiting on some help.

---

### Post by Seeker84 on 2007-06-11
Still waiting for some feedback

---

### Post by Seeker84 on 2007-06-13
Does anyone have any information about this?

---

### Post by Seeker84 on 2007-06-13
So here's what I've tried and found.

I tried xev, but when I pressed the Fn key it didn't register that it had been pressed.  But if I press the "F3" key it registers the "F3" key.  But if I wait to use number lock (Fn+F3) it registers something different.  So to me by it's self the Fn key isn't registered, only when combined with a known hotkey does it register.

Looking at today's posts I see a possibility for the function call I was wondering about.  I think I found it. located in /etc/acpi/wireless.sh.

Opening it up in text editor I see some interesting stuff.  I'll post it later but I don;t see a reference to LED just to power.

---

### Post by Seeker84 on 2007-06-13
So if anyone knows what any of these files do, let me know.  I'm looking through them and I does see the directories they mention.  IF the answer is as simple as re-write them with actual directories just say "yeah you lazy computer programmer, re-write those files."  I would though like to know what file is called when you toggle the WiFi.  But here are the files I'm looking at:

/etc/acpi/wireless.sh
/etc/acpi/asus-wireless.sh
and possibly /usr/share/acpi-support/state-funcs

I do not see:
/sys/class/net/device/power/state
I do see
/sys/class/net/eth1/device/power/state
I do not see dir wireless in /sys/class/net

I do not see:
/proc/acpi/asus
I do see
/proc/acpi

---

### Post by Thomar on 2007-06-13
If it helps...

Using a Satellite 105A, the Fn numpad on the keyboard works just fine.  However, none of the F# key commands work.  It looks like this is a hardware deal, something the keyboard itself does (as I've verified this behavior by setting up a simple Java echoer).

---

### Post by Seeker84 on 2007-06-15
I don't really want to get a new laptop, so I'm still looking into these files.  My current laptop is dell inspiron 700m. More feedback is required.

---

### Post by Seeker84 on 2007-06-15
So here's the files I'm working with:

this is /etc/acpi/wireless.sh
```

#!/bin/bash
# Find and enable/disable wireless devices

for DEVICE in /sys/class/net/*; do
#for DEVICE in /sys/class/net/eth1/*; do
     if [ -d $DEVICE/wireless ]; then
# $DEVICE is a wireless device. Check if it's powered on:
	if [ `cat $DEVICE/device/power/state` = 0 ]; then
# It's powered on. Switch it off.
	    echo -n 2 > $DEVICE/device/power/state;
	    #echo -n 0 > $DEVICE/device/led;
	    echo 0
	else
# It's powered off. Switch it on.
	    echo -n 0 > $DEVICE/device/power/state;
	    #echo -n 1 > $DEVICE/device/led;
	    echo 1
	fi
    fi
done

```

---

### Post by Seeker84 on 2007-06-15
this is asus-wireless.sh
```

#!/bin/bash
# Find and enable/disable wireless devices

state=`. /etc/acpi/wireless.sh`

if [ "$state" = "0" ]; then
      #echo -n 0 > /proc/acpi/asus/wled
      echo -n 0 > /asus/wled
else
      #echo -n 1 > /proc/acpi/asus/wled
      echo -n 1 > /asus/wled
fi

```

---

### Post by Seeker84 on 2007-06-18
Still waiting for some feedback.

---

### Post by Seeker84 on 2007-06-20
I'm still here, haven't gotten any further.

---

### Post by Seeker84 on 2007-06-21
Still here.

---

### Post by Seeker84 on 2007-07-07
I'm still here I haven't gotten any further, still hoping for some more feedback

---

