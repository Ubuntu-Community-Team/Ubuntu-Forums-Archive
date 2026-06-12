---
title: "lirc doesn't acknowledge my Vaio remote control"
date: 2013-09-09
forum: Hardware
---

### Post by sal02452 on 2013-09-09
I have an old remote control and USB remote control receiver from a Sony Vaio Media Center PC. The remote control says "RM-MC1". I can't say for sure that the remote control still fully works, but I know that it still does something, because whenever I press any button on the control, the LED on the front of the receiver comes on, and stays on as long as I hold down the button. So the remote control and the receiver are communicating, at least a bit.

"lsusb" says "Bus 003 Device 007: ID 045e:006d Microsoft Corp. eHome Remote Control Keyboard keys". So the receiver is recognized, at least a bit.

I installed lirc. When i run "irw", I get no output at all. I press all the remote control buttons, and the receiver LED flashes, but irw is completely silent. How can I try to debug this?

---

