---
title: "Elantech touchpad won't work (specifically ETPS/2)"
date: 2017-05-03
forum: Hardware
---

### Post by UbuntuWho on 2017-05-03
This is an issue I've had for over a year, with no solution yet. Ever since sometime last year when I had Ubuntu 14.04, my touchpad stopped working. The two buttons work fine, but I can't scroll, move the cursor, or do anything else. I know my laptop has an ETPS/2 type Elantech touchpad, and I ran across this post ([https://ubuntuforums.org/showthread.php?t=2241520](https://ubuntuforums.org/showthread.php?t=2241520)), but I'm wondering if there is a better, more permanent solution than having to apply a patch with every update. I'm on Ubuntu 16.04 now, with my touchpad still not working.

---

### Post by UbuntuWho on 2017-05-13
Never mind; I saw this: [https://askubuntu.com/questions/809034/16-04-elantech-touchpad-not-working-on-new-laptop#809040](https://askubuntu.com/questions/809034/16-04-elantech-touchpad-not-working-on-new-laptop#809040)

[LIST=1]
[*]Installed package xserver-xorg-input-libinput 
[*]Uninstalled xserver-xorg-input-evdev and xserver-xorg-input-synaptics (the latter was already uninstalled, actually) 
[*]Rebooted. 
[/LIST]
 Now it's working. Why didn't I just do my own original research?!? ](*,)Anyone else who has issues with this is welcome to post in this thread as long as it remains open.

---

