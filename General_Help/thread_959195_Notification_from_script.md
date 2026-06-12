---
title: "Notification from script"
date: 2008-10-26
forum: General Help
---

### Post by themuddler on 2008-10-26
Is there any way to pop up a system notification (preferably with a timeout) through a script?  I'd like to use it to display output from a script for a short period without the script having to open a terminal window.

Ideas gratefully received, thanks.

---

### Post by mister_pink on 2008-10-26
Try zenity. Its quite straightforward and probably exactly what you're after.

---

### Post by themuddler on 2008-10-26
Thanks, that'll serve the purpose - although it's not quite as nice as a timed notification at the top right of the screen it's still good enough for what I'm doing.

I can get quite close to a passive notification by using the following:

[command] ; sleep 3 | zenity --progress --pulsate --auto-close --text="Doing the command"

Cheers for the quick response!

---

### Post by lswb on 2008-10-26
The xmessage program is similar to zenity and it does have a timeout option as well as screen placement options. Unfortunately the boxes it pops up are kind of crude looking compared to zenity, but perhaps that can be configured. 

For simple informational popups that don't need to return a value, you can  background the zenity command in a script, then kill it from the script later, something like
```

zenity --options --other-options --etc &
sleep 3
kill %zenity

```

---

### Post by mister_pink on 2008-10-26
You could also try pynotify. You'll need to write some python in a separate script and then call that script from your shell one. I'll see if I can find an example for you then edit this post...

Edit: Here you go, note I claim no credit for this, its just from some scripts I used to use on my eeepc. Should be easy enough to tailor to your needs.

```

#!/usr/bin/env python
#
# Wifi toggle notification -- EeePC 900A/901/1000
# v1.3
# by elmurato
# Modified version from NiceeePC (https://launchpad.net/niceeepc)

import pygtk
pygtk.require('2.0')
import pynotify
import sys
import gtk
import os

if __name__ == '__main__':
	if not pynotify.init("Wifi Status"):
                print "Unable to initialize Python Notify"
		sys.exit(1)

	if len(sys.argv) != 2:
		print "USAGE: " + sys.argv[0] + " (on|off)"
		sys.exit(1)

	uri = "file:///usr/share/icons/gnome/scalable/devices/network-wireless.svg"

	if sys.argv[1] == "off":
		n = pynotify.Notification("WLAN", "Your wireless adapter has been <b><span color='red'>disabled</span></b>. ", uri)
	elif sys.argv[1] == "on":
		n = pynotify.Notification("WLAN", "Your wireless adapter has been <b><span color='green'>enabled</span></b>. ", uri)
	else:
		print "USAGE: " + sys.argv[0] + " (on|off)"
		sys.exit(1)
		
	n.set_timeout(3000)
	if not n.show():
		print "Failed to send notification"
		sys.exit(1)

```

---

