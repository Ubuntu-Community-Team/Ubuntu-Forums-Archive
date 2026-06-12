---
title: "nVidia card crashes desktop"
date: 2008-12-31
forum: Hardware
---

### Post by stageshocked23 on 2008-12-31
I'm having a bit of trouble with my video card, here's the situation.

I've installed Ubuntu 8.10 desktop 32 bit i386 on a 2ghz single core dell desktop. The installation process was very difficult, but eventually I got it to work by removing my nvidia geforce fx5200 card, changing the bios back to the integrated one, and installing in safe graphics mode.

While enduring the extremely terrible resolution, I completed all of the updates that synaptic brought up, and proceeded to get to work installing my video card. Here's what I did.

sudo apt-get install envyng-gtk

Then I shut down,
replaced the video card
reverted the bios to pci for video
rebooted the pc

The splash screen hung at about 2.5 "blocks" or whatever you want to call the little divided increments on the splash screen.

So I tried recovery mode, which halted with errors like:

run_program '/lib/udev/usb_id' abnormal exit
run_program: exec of program '/lib/udev/path_id' failed

modprobe also failed, and after a minute or two, I got:

kernel panic - not syncing attempting to kill init!



Any ideas? I just want my video card to work.

Thanks,
Shane

---

### Post by stageshocked23 on 2009-01-01
bump

---

