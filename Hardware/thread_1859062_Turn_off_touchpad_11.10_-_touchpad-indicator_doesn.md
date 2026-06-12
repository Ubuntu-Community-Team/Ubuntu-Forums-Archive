---
title: "Turn off touchpad 11.10 - touchpad-indicator doesn't work"
date: 2011-10-13
forum: Hardware
---

### Post by gregalynch on 2011-10-13
I just upgraded to oneiric and I need to be able to turn off my touchpad so that I can type.  I saw a number of posts saying to do this with touchpad-indicator.  I installed it, and originally it showed up in the upper panel, but I couldn't get it to actually disable the touchpad.

After a restart, now the little touchpad icon doesn't even appear when I run touchpad-indicator.  

Is there another way to make this work?

Using the standard touchpad on hp pavilion dm4t

also, i noticed that when I ran lsusb the touchpad doesn't seem to show up.  should it?

---

### Post by gregalynch on 2011-10-13
OK, I figured out that I can turn it on and off by running:

xinput set-prop 12 "Device Enabled" 0

or 1 for turning it on.

What would the script be that would toggle this on and off?  I don't know enough to write it myself.  If I had one I could assign it to a keystroke and problem would be solved.

Thanks

---

### Post by gregalynch on 2011-10-13
Nevermind - I found it here:

[https://help.ubuntu.com/community/SynapticsTouchpad/ShortcutKey](https://help.ubuntu.com/community/SynapticsTouchpad/ShortcutKey)

In case anyone else wants to do this: go to the 'Using Xinput' part at the bottom.  The script they give finds the device ID number for you, or you can find it yourself, do away with the first part of the code, and just replace the tp_id variable with the constant (this is what I did).  Works great now.

---

### Post by lancest on 2011-10-13
How is this script called? From Gnome startup?

---

### Post by gregalynch on 2011-10-14
I'm not quite sure what you're asking for here. (I don't know the technical jargon for most of this - I'm still kind of a newbie)

So here are some potential answers:

1)

It's run with /bin/sh (bash?), so the first line of the script should be #! /bin/sh 

2)

To get it to work:
a) I saved the script as touchpad-toggle in a scripts folder in my home directory
b) I added that folder to my path file
c) If you go to the dash and find the 'keyboard' settings app, you can go to the 'shortcuts' tab and set custom keystrokes.  I set it up so that Alt+t runs the command touchpad-toggle.  So now I can turn the touchpad on and off just with my keyboard.

Sorry if the above is all stuff you know already - its pretty new to me.

---

