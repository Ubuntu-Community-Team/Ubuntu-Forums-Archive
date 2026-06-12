---
title: "Logitech MX510 + logitech_applet:  run on startup?"
date: 2005-09-12
forum: Hardware &amp; Laptops
---

### Post by Brunellus on 2005-09-12
I have a Logitech MX510 mouse, and I'd like to run the logitech_applet on startup to set the cruise control to "on" and set resolution at 800cpi.

I suspect the script would look something like this:
```

#!/bin/sh
#A script to load the Logitech Mouse Applet 
logitech_applet -e -s 800
```

where/when would I run this so that it executes when X starts?

---

### Post by endy on 2005-09-14
I have just written a guide, part of which (Section 3, part 3) explains one solution to this.

[http://ubuntuforums.org/showthread.php?p=350088#post350088](http://ubuntuforums.org/showthread.php?p=350088#post350088)

HTH :)

---

### Post by Simon80 on 2007-01-13
It's a shame I didn't post this sooner, but the proper way to do this sort of thing is not on boot, but whenever a device gets hotplugged.  To do this, you write a udev rule and put it in any file in /etc/udev/rules.d. I can understand why you did it your way, I did that for a while until I figured out how to write udev rules.

As an example, I've uploaded what I use.  Just drop this into /etc/udev/rules.d and remove the .txt from the end, and logitech_applet will run whenever a Logitech mouse is plugged in.

---

