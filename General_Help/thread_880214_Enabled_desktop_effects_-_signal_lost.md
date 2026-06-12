---
title: "Enabled desktop effects - signal lost"
date: 2008-08-04
forum: General Help
---

### Post by project6 on 2008-08-04
Hi.

Among the first things I did as I entered Ubuntu was browsing around trying different things. I clicked to enable desktop effects, a file got downloaded (Nvidia something) and then I rebooted.

Now my monitor doesn't have a signal when I boot Ubuntu.

What should I do? I'm not extremely skilled with Linux, I tried to boot in recovery mode and got into a shell prompt but I don't know where to go and what to edit in order to restore things as they were. I'm not quite familiar with the syntax either, but I guess I could browse to some kind of config file and disable the effects? (using 'cd' command?)

best regards,
p6

---

### Post by UbuntuNerd on 2008-08-04
your X server may not be running right do CTRL-ALT-F1 and see if the text login appears or it is running at the wrong refresh rate/resolution

---

### Post by UbuntuNerd on 2008-08-04
assuming you do see your bootloader (Grub).. you can try to Boot in/safe-mode and try to reconfigure your X-setup 

dpkg-reconfigre xserver-xorg

---

### Post by project6 on 2008-08-05
Thanks, I simply clicked "Try to fix X server" and it reconfigured and now I can enter Ubuntu again.

What do I have to do to get the effects working? Do I need to install a driver for my GPU first?

---

### Post by UbuntuNerd on 2008-08-05
Im sure your problem had something to do with the way you downloaded your nvidia drivers try using this guide to enable your drivers and desktop effects also install compiz good luck

[http://thegabfather.wordpress.com/2008/05/17/how-to-install-compiz-fusion-in-ubuntu-hardy-heron/]("http://thegabfather.wordpress.com/2008/05/17/how-to-install-compiz-fusion-in-ubuntu-hardy-heron/")

---

### Post by project6 on 2008-08-05
Thanks for your reply.

I've tried a dozen of tutorials on how to enable desktop effects, however as soon as I check "enabled" in hardware drivers, and reboot, Ubuntu goes into low graphics mode or the screen gets no signal at all.

I don't know what I'm doing wrong, maybe I have a super special GPU that is not supported by Ubuntu...

I tried for several hours now and I always end up booting in recovery mode and resetting x server to get my GUI back.

I have a GeForce 600XT card, AGP.

Any help is greatly appreciated... thanks
/p6

---

