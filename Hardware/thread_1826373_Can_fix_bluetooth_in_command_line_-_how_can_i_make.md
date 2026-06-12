---
title: "Can fix bluetooth in command line - how can i make permanent?"
date: 2011-08-16
forum: Hardware
---

### Post by rbeer on 2011-08-16
I have a USB bluetooth dongle attached to my laptop. Whenever I turn on the laptop the bluetooth settings are greyed out and just presents me a GUI button for turn bluetooth on. Pressing this doesn't do anything and eventually reverts back to unpressed.

However if I enter "sudo hciconfig hci0 up" at the terminal it springs into life. I'd like to add a line to do this at startup but I'm stumped at how to do this because of the sudo requirement.

Alternatively am I looking at this from the wrong angle and could do something else to fix it?

---

### Post by jerrrys on 2011-08-17
i do not use bluetooth, but had a thought.  hciconfig is owned by root (of course).  what happens if you change owner (permissions) to yourself (user)?

---

### Post by rbeer on 2011-08-19
Neat idea. I've changed it and added to startup but won't know until I reboot. WIll update when I find out.

---

### Post by rbeer on 2011-08-22
No luck. Changed owner of the file but still needs SUDO to run.

Back to the drawing board.

---

