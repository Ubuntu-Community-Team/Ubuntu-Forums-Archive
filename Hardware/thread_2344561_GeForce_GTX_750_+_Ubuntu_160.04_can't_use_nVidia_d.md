---
title: "GeForce GTX 750 + Ubuntu 160.04: can't use nVidia driver newer than 358?"
date: 2016-11-26
forum: Hardware
---

### Post by sremick on 2016-11-26
So at some point in the past, during normal updating my video driver broke and I had to switch back to the Nouveau driver. Been meaning to look into this and finally tried switching back to the nVidia driver last night but was getting the same behavior. Figured I'd look into it more systematically and tried running through each version. By doing that I discovered that nothing newer than version 358 (358.16) works. I tried 364, 367, 370 and 375. Interestingly, version 375 is the one that the nVidia site says is recommended for this card, and some Google searching turned out people reporting that version 375 fixed a lot of the issues in previous versions.

I am running Ubuntu (well, Xubuntu) 16.04, an Asus GeForce GTX 750 card, and I've installed the Proprietary GPU Drivers PPA (ppa:graphics-drivers/ppa). I try switching via the Additional Drivers control.

What happens with the newer versions is that they apply fine, then I reboot. It gets as far as the graphical LUKS encryption prompt (I use full-disk encyrption), however this screen is low-res, much lower than normal (it usually runs at native resolution), and it seems "frozen"... typing the password doesn't seem to do anything. I can CTRL-ALT-F1 to another terminal in which there's just a flashing cursor... doing CTRL-ALT-F7 takes me to a screen where the password I was trying to type appears in cleartext on a white-on-black terminal screen (!!!). The computer responds properly to a CTRL-ALT-DEL soft reboot and does a clean shutdown. I reboot and this time (after the grub screen, I assume because it detected an unsuccessful boot) get brought straight to just the white flashing cursor on a black screen (no LUKS prompt). I can again CTRL-ALT-DEL, boot into a recovery boot, drop to terminal and purge the nvidia drivers to switch back to Nouveau so that I can try another version.

Rinse, repeat... I went through all that starting with v375 and stepping backwards. It wasn't until I hit 358 that I could boot successfully using the nVidia proprietary driver.

So, I'm functional, but... why am I stuck on such an old version? I'd imagine it'd be good to stay current for bug fixes and performance improvements (I do some light 3D gaming). Any thoughts? Thanks!

---

### Post by Yellow Pasque on 2016-11-26
Can you give your current /var/log/Xorg.0.log so we can see some details? Was this a fresh install or an upgrade from a previous Xubuntu?

---

### Post by sremick on 2016-11-26
> **Temüjin said:**
> Can you give your current /var/log/Xorg.0.log so we can see some details? 

Sure, see attached. Let me know if you need more logs or a copy of it right after me doing something specific.

> Was this a fresh install or an upgrade from a previous Xubuntu?

It was an upgrade. This computer has gone through a number of upgrades.

---

### Post by Yellow Pasque on 2016-11-26
That log looks okay (which I expected). Next, is to try to get a log from a failed start.

Also, this looks like it could be related: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-367/+bug/1643345](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-367/+bug/1643345)

---

