---
title: "Screen is now gibberish and boy do I feel stupid......"
date: 2008-09-07
forum: Hardware
---

### Post by BigGeoff on 2008-09-07
I feel a complete idiot!
When I installed Gutsy 6 months ago I allowed it to autodetect the display settings which have worked fine. Today I discovered that it had my exact monitor in the settings so I told it to use that and now I can't see anything on the screen therefor can't even try to sort out the error.

My question is, can I reboot into recovery mode and reset something in terminal that will tell the system to autodetect itself rather than use the messed up settings it is using at the moment? Be aware I am virtually a Terminal virgin.

---

### Post by cdtech on 2008-09-07
Sure, in recovery mode just type this on a command line:
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by BigGeoff on 2008-09-07
Thanks cdtech, I can at least see what the hell I am doing even though it's in low res mode.

Geoff

---

### Post by cdtech on 2008-09-07
Good, at least now you can modify your xorg or use a program to set your display.

---

