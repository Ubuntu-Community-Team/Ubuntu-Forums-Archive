---
title: "Installing on a Laptop with a Broken LCD"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by brettc on 2009-05-04
Hi all,

I have an old Compaq Presario 900 with XP home installed on it. It has a broken LCD, but still works fine. I've downloaded the latest Xubuntu to install on it. I intend to use it headless, via SSH, to run some simulations whilst I'm working. 

Can anyone tell me how I can go through the install via an external monitor?

Currently, the screens are mirrored and I get the first round of language selection + options (though only the F1 key seems to actually work). I get an install screen for a while, and then nothing. I take it that this is when it switches into graphics mode with X for the rest of the install. 

There is a key that switches the monitor setup, but I guess this only works in windows (?)

NOTE : I am not a complete newbie, but my linux knowledge is limited.

Any help appreciated!
Thanks,
Brett

---

### Post by yeats on 2009-05-04
If you're running headless, why not go for Ubuntu Server?

---

### Post by redxine on 2009-05-04
If X is trying to load on the primary monitor.... take a look at your BIOS configuration. There might be an option that lets you select between using the primary monitor and the secondary output. If not, you could try editing the /etc/X11/xorg.conf file before X starts up in one of the different tty consoles when it prompts for Language and such. Try Ctrl+Alt+F2/F3 (I forget what one has the root shell on it) and run nano /etc/X11/xorg.conf . Look for the video card entry/ies

If all that fails, there may be the option of installing it on a different computer by removing the hard drive.

---

### Post by Marvin666 on 2009-05-04
I believe F2 is the root shell.

---

### Post by brettc on 2009-05-05
Hi. Thanks for the suggestions. The bios has no video options, so that's out. I'll see what I can do with looking at the .conf. Any suggestions as to what I should be changing things from/to? Anyway, I'll go dig around...

Thanks!
Brett

---

