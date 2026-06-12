---
title: "C840 - Display Issues after closing and opening the lid."
date: 2006-10-01
forum: Hardware &amp; Laptops
---

### Post by eniacpx on 2006-10-01
I have a Dell C840. I love it it works great with Ubuntu. EXCEPT it doesn't turn off the display when I close it. I have figured out how to get that to happen now, using the vbetool dpms command, but now when I open the lid the display comes on, but it is streched. It looks like the height stays the same, but the horizontal resolution is doubled. This happens unless gnome-screensaver has put the display to sleep. When it does happen it can be fixed by doing Alt+Ctrl+F6, then Alt+Ctrl+F7.

What I need:
-Some way to correct the resolution via a script.
OR
-The ability to run the gnome-screensaver sleep command befor it turns the display off.

---

### Post by xyz on 2006-10-02
> **eniacpx said:**
> I have a Dell C840. I love it it works great with Ubuntu. EXCEPT it doesn't turn off the display when I close it. I have figured out how to get that to happen now, using the vbetool dpms command, but now when I open the lid the display comes on, but it is streched. It looks like the height stays the same, but the horizontal resolution is doubled. This happens unless gnome-screensaver has put the display to sleep. When it does happen it can be fixed by doing Alt+Ctrl+F6, then Alt+Ctrl+F7.

What I need:
-Some way to correct the resolution via a script.
OR
-The ability to run the gnome-screensaver sleep command befor it turns the display off.
Don't know if this'll work for you as I have a Toshiba Satellite A 40...
To suspend I run as root:
```
echo -n mem > /sys/power/state

```
and to resume I keep a finger on any key for a couple of seconds.
There's a link on that in my sig. That's how I got it to work for me.
Let me know...

---

