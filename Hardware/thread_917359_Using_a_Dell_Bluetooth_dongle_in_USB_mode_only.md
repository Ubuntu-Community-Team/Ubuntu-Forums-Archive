---
title: "Using a Dell Bluetooth dongle in USB mode only"
date: 2008-09-11
forum: Hardware
---

### Post by sread on 2008-09-11
Hi,
I'm using a Dell bluetooth keyboard and mouse on a mac mini, which is dual booted with Ubuntu and OS X. The mini has a built in bluetooth module, which seems to be fine, I don't really have a use for it. What I want to do is use the dongle which came with the keyboard, but not as a bluetooth dongle. This is because I don't want to have to re-connect the keyboard with a different keycode and all that jazz everytime I switch OSs.

Currently, using the dongle under both Ubuntu and OSX, the keyboard and mouse are recognized just as regular USB interface devices. The problem starts when Ubuntu boots, and assigns the module as a bluetooth dongle instead. This means when I reach the login screen, I need to unplug and re-plugin the dongle, after which it acts as a USB mouse/keyboard.

So to sum up: under Ubuntu the dongle is recognized as a bluetooth device on boot, but I don't want it to be! Any ideas?

Thanks,
Stuart

---

### Post by Thyferran on 2008-11-29
I was having the same trouble with my machine so I simply removed all the bluetooth packages from the system as I don't have any other bluetooth devices for this machine. Not the best solution but it does work.

---

