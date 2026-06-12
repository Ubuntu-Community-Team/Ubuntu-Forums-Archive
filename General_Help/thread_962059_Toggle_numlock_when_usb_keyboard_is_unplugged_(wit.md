---
title: "Toggle numlock when usb keyboard is unplugged (with udev)"
date: 2008-10-28
forum: General Help
---

### Post by Parksy on 2008-10-28
I usually use my laptop with a usb keyboard, but sometimes unplug it when I use my laptop in the living room.  My problem is that numlock turns part of the built in keyboard into a number pad so I'd like to turn off numlock whenever the external keyboard is unplugged.

I created a bash script for udev to run with the keyboard is unplugged, but numlock always returns an error in the script. (The $? variable is always 1.)  My guess is that there's some environment problem, so numlockx doesn't see that Xorg is running. (Since it's supposed to be run in an Xorg startup script).  Any ideas on how to get it to work correctly?

---

### Post by cosmodemonictel on 2010-11-13
I'm having the same issue. Running a linksys key board with a num lock key pad into an asus laptop that doesn't have num lock. When I reboot the computer the num lock configuration is copied over the right hand side of the keyboard on the laptop. Any suggestions on how to fix this?

---

