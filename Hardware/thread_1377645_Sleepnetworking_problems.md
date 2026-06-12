---
title: "Sleep/networking problems"
date: 2010-01-10
forum: Hardware
---

### Post by sloom22 on 2010-01-10
I recently upgraded Ubuntu from 9.04 to 9.10 on my Lenovo G530 laptop. Since upgrading, if I close the lid to go to sleep and then open it, after opening I cannot connect to wireless networks. They show up correctly, but when I connect the connection stalls on “Obtaining IP Address”. I have to restart to get wireless to work again.

I have switched the GNOME wireless manager for WICD, it didn't affect things.

I found one suggestion online for fixing the problem. Based on this I went to /etc/pm/config.d/00sleep_module and added a line SUSPEND_MODULES="wl" where “wl” is what I guessed was the name of the wireless driver. This actually fixed the problem, but caused another one. Now, upon waking up from sleep, the laptop often freezes. The whole screen is black except for a cursor in the upper left corner and the mouse pointer at some random location, which cannot be moved. The caps/scroll lock lights blink constantly, and disconnecting the power cord causes a “low battery” beep though the battery is charged. Restart (and ctrl-alt-backspace X restart) doesn't work, I have to manually remove the battery.

Any ideas how to fix these problems? (I.E. fix the networking problem so that the sleep problem can be avoided, or vice versa?)

Thanks!

---

### Post by waj1122 on 2010-03-27
This may not apply to you but after the last kernel upgrade I have to run these commands after suspend to get wireless working again without rebooting.
modprobe -r ath5k
modprobe ath5k

---

### Post by sloom22 on 2010-05-18
waj1122:

Based on your advice I ran:

sudo modprobe -r wl
sudo modprobe wl

and wireless works after sleep! Now I just have to figure out how to do this automatically.

BTW I have a Broadcom BCM5906M wireless card. (thank you to the lshw, lspci commands)

---

### Post by waj1122 on 2010-05-20
Here's what I did:
Create a file named 1net
Paste the following into it:

#!/bin/sh
modprobe -r ath5k
modprobe ath5k

Save the file and make sure it's executable.

Put this in /usr/bin and have it run on startup.

Or just click on it to run it.

---

