---
title: "Help: BT mouse connects but doesn't work."
date: 2024-11-28
forum: Hardware
---

### Post by BeachNerd on 2024-11-28
Ubuntu 24.04.1 LTS, BT mouse configured using Blueman Applet 2.35.   Using generic , no dongle BT mouse, which was working fine and (maybe) stopped working with a recent OS component update as I haven't changed anything that I'm aware of.  The mouse is charged and connectes and works fine on other devices but when connected to Ubuntu, it connects but doesnt function.  Occasionaly, I get a connection error message:  "Connection Failed: br-connection-create-socket", even though i get a popup indicating the mouse is connected.  I've tried deleting the mouse and reconnecting several times and it connnects but doesn't work .

Edit:  Interesting if I put the lapto to sleep, when it wakes, there's a popup indicating the mouse connects, even though power to the mouse isn't turned on.   A short time later, there's another popup indicating the mouse has disconnected.

---

### Post by BeachNerd on 2024-11-30
Things are getting worse.  Got another BT mouse to connect, and it was working fine for a couple of day, but now that mouse also shows as  connected  but no longer functions.  Bluetoot monitor running very, very slow and constantly hangs.  Meanwhile, other BT devices, eg, headset, continue to work fine.  Kind  of at my whits end.  Next stop will be to dry reinstalling Ubuntu - clearly a huge PITA.

---

### Post by BeachNerd on 2024-11-30
Update: Running the following commands got the mouse to work again - not immediately, but after a bit, it stated working


bluetoothctl
[bluetooth]# scan on
# Wait and identify your device in the list
[bluetooth]# scan off
[bluetooth]# pair <device_id>
[bluetooth]# trust <device_id>
[bluetooth]# connect <device_id>
[bluetooth]# exit

---

### Post by him610 on 2024-11-30
FWIW, I purchased a couple of bluetooth mice a couple or years ago. Never could get either to consistently connect. Finally, trashed both of them.
If you want a wireless mouse, suggest you look at Logitech wireless mice. I have several; never any issues.

---

### Post by BeachNerd on 2024-11-30
> **him610 said:**
> FWIW, I purchased a couple of bluetooth mice a couple or years ago. Never could get either to consistently connect. Finally, trashed both of them.
If you want a wireless mouse, suggest you look at Logitech wireless mice. I have several; never any issues.

The mouse that conncted but stopped working was working fine for months, so not sure what made it go south (and not sure why the comman line fix worked when nothing else seemed to fix it).  I've got a bunch of Logitech mice with Universal receivers that I know will work but I prefer to skip the need for a dongle/tying up a USB port. 

To make this weirder, when my original BT mouse stopped working, I switched to another BT mouse and it worked fine, until this morning at which point it ended up with the same symptoms as the original mouse.  

It gets weirder still: the mouse that would connect, but not work, displayed exactly the same symptoms on a totally different laptop running the same version of Ubuntu. That mouse had been working flawlessly on that machine for months as well.  This is what made me think whatever happend was due to a recent OS update.

---

