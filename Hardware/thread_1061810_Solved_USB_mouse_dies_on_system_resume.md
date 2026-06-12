---
title: "Solved: USB mouse dies on system resume"
date: 2009-02-06
forum: Hardware
---

### Post by andrewmv on 2009-02-06
Here's the solution I found to an issue I was having with USB mice on my laptop.

I'm Ubuntu 8.10 / Ibex on a Dell Latitude D510 (which has had a number of other suspend and power management quirks), using a wireless USB Kensington Slimblade Media Mouse.

The mouse works find on cold boot and hotplug, but when I suspend the system to RAM and then resume it, the mouse always failed to come back.  I'd have to reset it by re-plugging it, or running

```
modprobe -r usbhid && modprobe usbhid
```

as root to re-initialize all USB human input devices.

It seemed like this module wasn't suspending correctly, so I wanted to add it to the list of modules to be automatically unloaded before suspend.

I tried modifying the hooks in /etc/acpi/suspend.d and /etc/acpi/resume.d, but none of them seemed to ever actually get called.

I successfully solved this problem by adding a one line configuration file to the /etc/pm/config.d directory, adding the usbhid module to the $SUSPEND_MODULES list:

```
echo 'SUSPEND_MODULES="$SUSPEND_MODULES usbhid"' > /etc/pm/config.d/90reload_mouse
```

Now the usbhid module is unloaded before sleep, and automatically re-inserted during resume.

I suspect this is a laptop or distribution rather than a mouse issue, though I haven't had the opportunity to try to recreate the problem with other HID devices.

---

### Post by Saul Howard on 2009-02-17
Brilliant. This worked for me straight away on my Dell Inspiron 6400 (e1505).

By the way, have to run this as root, of course, and you'd have to rewrite the command with **tee** or something to use **sudo**. I used **sudo -s** to start root shell and run the command.

---

### Post by rmgk10 on 2009-04-13
I have the same problem on a new Dell Vostro 1510 but the fix has not worked for me yet. My unix skills are very rusty so maybe I am doing something wrong.

I managed to get the 90reload_mouse file into the /etc/pm/config.d directory and its contents are: SUSPEND_MODULES="$SUSPEND_MODULES usbhid"

Am I misinterpreting something?

I installed ubuntu using Wubi.

---

