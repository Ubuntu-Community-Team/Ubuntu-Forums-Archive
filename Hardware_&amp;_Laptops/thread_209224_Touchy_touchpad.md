---
title: "Touchy touchpad?"
date: 2006-07-04
forum: Hardware &amp; Laptops
---

### Post by bwgolling on 2006-07-04
I wonder if anyone has an answer concerning a Toshiba M45.  Within Windows I can configure the touchpad to simulate holding the button down with a tap and hold.  I cannot seem to figure out how to do this on Ubuntu.  Any suggestions?
Tks
bwgolling

---

### Post by cracker on 2006-07-05
The best way is to edit xorg.conf. Use this page for all the options, and what they do: [http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Synaptic_Options](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad#Synaptic_Options)
The file is at /etc/X11/xorg.conf and requires root privileges. After saving, you must restart X for changes to take effect. This can be done very quickly by pressing CTRL+ALT+BACKSPACE.

There are utilities to assist in configuring, but I've yet to get a single one to work, myself.

---

