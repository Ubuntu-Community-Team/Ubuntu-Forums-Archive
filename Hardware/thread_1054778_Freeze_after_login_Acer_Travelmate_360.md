---
title: "Freeze after login Acer Travelmate 360"
date: 2009-01-30
forum: Hardware
---

### Post by martinnut on 2009-01-30
Just starting out so please bear with me :)

Make: Acer Travelmate 360 - TM361EV
Model: MS2105
Ram: 512mb
HD: 30gig
Wireless: Dlink DWL-G650+ PCMCIA Wireless H/W B1 F/W 1.0.11

Trying to install Desktop 8.10 32bit version to this old Acer. It normally runs XP fine, so its fully functioning. All onboard devices (Serial, IRDA and Parallel port) are Disabled in the BIOS.

Installation of Intrepid goes fine and it restarts. Login box appears on orange background, I can login, but after login is accepted, the screen goes black and a wait pointer appears.  Tried with an external monitor and the same thing occurs. Left the laptop on overnight, but it stays on this screen.

CTRL-ALT-BACKSPACE, CTRL-ALT-DEL or any of the other terminal Alt windows wont open, and Scroll lock or Caps lock are NOT flashing.  The mouse still moves the pointer around, but the icon is no longer rotating which doesnt indicate the machine is frozen. The CD works fine as I tried it on a newer laptop without a hitch.

I tried the previous version 8.04.2 and I can get to the Desktop fine, but after configuring my wireless the applications freeze, although the menus work ok.

What can I do to start to troubleshoot? are there any log files I can check out to see why this is happening?

Many thanks in advance :)

Regards

Martinnut

---

### Post by martinnut on 2009-01-31
Got my laptop booting to the desktop now finally :D

The fix was that I removed compiz as i read from another post this can cause problems with older Intel graphics chipsets.

I did the following commands at the GRUB recovery console (pressed ESC before booting)

sudo apt-get remove compiz
sudo apt-get remove compiz-core

Cheers guys
Martinnnut

---

