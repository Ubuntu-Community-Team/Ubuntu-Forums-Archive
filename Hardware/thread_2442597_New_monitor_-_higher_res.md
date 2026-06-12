---
title: "New monitor - higher res"
date: 2020-05-05
forum: Hardware
---

### Post by william_nbg on 2020-05-05
Hello,
My new monitor arrived today, it has a higher resolution 1440 while my old one was 1080. I hooked it up and booted. Grub comes up but after I only get a blank screen. I booted up in safe mode, which works, but is fixed and a low resolution. and rebooting drops back to black screen. If I boot up to my Ubuntu 20.04 USB drive (for installing) it accepts the higher resolution and looks/act fine. Now, I'm at a loss??

When I'm in black screen ctrl alt f1 doesn't work either.

---

### Post by Autodave on 2020-05-05
Can you please give us some info on your hardware: especially the video card.  Did you install and video drivers?  If so, what one(s) and where did you get them from?

---

### Post by william_nbg on 2020-05-05
I'm using an on board amd chip, I forgot the exact one. I don't have any special graphic driver installed just the default one. I have win 7 on a separate drive, I booted to (first time in a long time) and it starts. And when I boot to my ubuntu usb drive it works fine, too - at the higher res.

---

### Post by CelticWarrior on 2020-05-05
Try booting in "safe mode" (whatever that is), fully update the system and also run ```
sudo update-grub
```

---

### Post by william_nbg on 2020-05-05
Sorry, 'recovery mode'
I tried it, but same thing happens. I reboot, grub, black screen

---

### Post by william_nbg on 2020-05-05
Since it worked using the Live USB drive, I even tried reinstalling Ubuntu, but the same thing happened after the initial reboot.

---

### Post by Autodave on 2020-05-05
What did you reinstall: 18.04 or 20.04?

---

### Post by william_nbg on 2020-05-06
Thanks a lot for your support. I noticed while running 20.04 live from usb drive that that display was running at 30Hz only. I'm starting to realize that my amd graphic chip just isn't up to running at a higher resolution. I've decided to hold off on the bigger monitor until I upgrade my computer (next year) and one with a better graphic card. I mark this thread as solved - again thanks a lot for your help.

---

