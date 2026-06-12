---
title: "[SOLVED] Laptop keyboard unresponsive after login"
date: 2008-10-01
forum: General Help
---

### Post by DataMonkey on 2008-10-01
Hi

I've been running Kubuntu Gutsy on my Dell latitude d620 for more than a year with very few problems. Today during a KDE session the keyboard stopped responding. I was browsing in firefox with a few terminals and emacs sessions open. The mouse still works (both on-board and usb) so i restarted X and then rebooted when that didn't work. Still no keyboard.

The keyboard works fine through grub and logging in to KDE and then for a bit while KDE is starting. It stops just as the splash screen changes to the desktop. I thought it must be the xorg.conf somehow, but i ran dpkg-reconfigure to create a new one with no change.

Any ideas as to what it might be?

Cheers

---

### Post by Gevarah on 2008-10-01
Perhaps, the port where your Keyboard plugs into the MB is loose. happened to me but you probably alreasy checked that out. : / haha. Try using a USB Keyboard if your connection is fine.

---

### Post by DataMonkey on 2008-10-01
thanks for the reply- it's definitely a software issue though. The keyboard works fine until the desktop is loaded.

---

### Post by DataMonkey on 2008-10-02
Stupid mistake- somehow I switched on slow-keys without noticing. Too much coffee not enough sleep.
cheers

---

### Post by bcooperb on 2008-10-06
Data, This sounds just like what happened to me. It would work fine while I was logging in and on the LiveCD, but when i booted to the desktop then I couldn't type...I couldn't even use the virtual keyboard!..You said you had Slow Typing turned on? And that was your issue? Was anything else wrong? how do I turn that on and off? Thanks!

====================================================

After I learned of the "Slow Keys" feature from you Data I dug a little deeper... Here is what I found for you others out there that might have this prob!

[https://bugs.launchpad.net/ubuntu/+bug/41427]("https://bugs.launchpad.net/ubuntu/+bug/41427")

---

### Post by DataMonkey on 2008-10-06
Thanks for that bcooperb- nice to know i'm not the only one that's been stumped by that problem!

---

