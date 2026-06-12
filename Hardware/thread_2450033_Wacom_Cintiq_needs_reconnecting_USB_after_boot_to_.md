---
title: "Wacom Cintiq needs reconnecting USB after boot to work"
date: 2020-09-06
forum: Hardware
---

### Post by ragtag on 2020-09-06
I bought a used Wacom Cintniq 27, and it works fine in Ubuntu 20.04, as long as I unplug and re-plug in the USB after the machine has booted up (before or after login doesn't matter). If I don't do that, the pen simply doesn't work, but xinput and xsetwacom still list the stylus input device, and it looks like it's loaded in the logs.

I'm thinking there is something going on with the boot order, where the tablet loads before the driver, but I'm not sure what or how to debug/fix it. Any ideas?


(This is also possibly related to an issue I've had with my tablet PC recently, where the touch screen stopped working, but would work again if I put the laptop to sleep and woke it again.)

---

