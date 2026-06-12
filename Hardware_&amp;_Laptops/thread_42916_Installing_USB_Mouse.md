---
title: "Installing USB Mouse"
date: 2005-06-19
forum: Hardware &amp; Laptops
---

### Post by drdeutsch on 2005-06-19
I haven't seen any how-to's that dealt with this problem, so I'm posting it here.

I use a BenQ M310 USB mouse with my Dell 8600 running Hoary Hedgehog.  If I boot up/restart with the usb key inserted, the load will stall after I type in my username and password. It will then continue after I remove the usb key.

Also, if I plug in my USB key after the desktop has loaded, it will take approximately 10 seconds until I am able to use my mouse.   Occasionally, if I"m typing or doing terminal work and haven't used my mouse, it will stall for a second if I move it and then track smoothly again.

Is there any way to prevent these problems, i.e. stop the mouse from stalling and also for the kernel to recognize the mouse on startup/reboot?

Total newb to Linux! Help is appreciated!
drdeutsch

---

### Post by diebels on 2005-06-19
You could try editing /etc/X11/xorg.conf to use another mouse-driver. And see dmesg and /var/log/messages for info on what happens when plugging/unplugging

---

### Post by drdeutsch on 2005-06-19
okay. How do I do that? :)

I've been using Linux for about 2 days now, so I need complete command lines, etc. for editing/viewing/doing anything to files via terminal.

Thanks,
drdeutsch

---

