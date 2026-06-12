---
title: "ooth keyboard and mouse issues in Intrepid 8.10"
date: 2008-11-11
forum: Hardware
---

### Post by painterh on 2008-11-11
My MS Bluetooth Elite Keyboard and mouse were working fine until I upgraded to Intrepid.  In Hardy I had edited the /etc/default/bluetooth file in order to make my keyboard and mouse pair on start-up.  This worked pretty well except that it would only pair if the computer was shutdown and restarted.  If I tried to just re-start instead of shutting down, it would result in no mouse or keyboard until I ran "hidd --search" from a terminal.  Now since upgrading to Intrepid my mouse and keyboard are easily set up using Intrepid's new bluetooth applet, but on boot-up it takes eight or ten seconds for them to come to life, and then only after I hit a key on the keyboard numerous times and move the mouse around for 5-8 seconds.  This behavior is repeated every time the mouse and/or keyboard sits idle for a few minutes.  Intrepid appears to use a different way to setup these devices, because when I look for the /etc/default/bluetooth file it has been renamed to "old".  The new bluetooth tools are nice but this behavior is extremely irritating.  If anyone has any ideas of how to keep the mouse and keyboard from going to sleep, I'd be appreciative.

---

