---
title: "How to turn off card reader to save battery"
date: 2011-05-03
forum: Hardware
---

### Post by Axx83 on 2011-05-03
Hi guys. My acer travelmate 8172t with Natty has a generic card reader attached to a usb port that is always on and consuming power.

Since I never need it (or very rarely) i turn it off with the "disk utility" program of Ubuntu and that seems to work.

I don't know which command the program launches and I would like to find out and put a script that disconnects the reader automatically on battery mode.

What I found so far is that if I run "dmesg | tail -20" and use the program the output is:
[ 4220.505262] WARNING! power/level is deprecated; use power/control instead
[ 4220.603444] usb 2-1.6: USB disconnect, address 3
but I don't understand exactly what command is run.

Please help

---

