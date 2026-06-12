---
title: "xorg problems"
date: 2007-06-29
forum: Hardware &amp; Laptops
---

### Post by rkrug on 2007-06-29
Ok, so on my computer the video card was clearly going bad, so I figured, hey, why not just take the hard drive from that computer (the one with ubuntu installed on it) and the DVD drive and put them in another computer?

So I did that, and now when I start up the computer (the new one), I get the xorg "blue screen of death", which says:

no devices detected
fatal server error 
no screens found

and a lot of other stuff. How do I fix this?

Thanks,
rob

---

### Post by nick_h on 2007-06-29
Your video card has changed so you will need to reconfigure the X server.

I suggest that you take a backup of your /etc/X11/xorg.conf and then run:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by rkrug on 2007-06-29
> **nick_h said:**
> Your video card has changed so you will need to reconfigure the X server.

I suggest that you take a backup of your /etc/X11/xorg.conf and then run:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

When I try to enter command (into the black screen that follows the blue screen) the words that I type show up but nothing happens.

---

### Post by nick_h on 2007-06-29
Type Ctrl-Alt F1 to switch to another console and then login.

---

### Post by rkrug on 2007-06-29
I did ctrl alt f1 but nothing happened

---

### Post by rkrug on 2007-06-29
Ok, I tried that, but after a few steps in the reconfiguration it says:

xserver-xorg postinst warning: overwriting possibly customized configuration file backup in /etc/x11/xorg.conf.20070629095317

---

### Post by nick_h on 2007-06-29
You can always select recovery mode from the grub menu if you really can't get to a terminal.

The command will overwrite /etc/X11/xorg.conf - that is why I suggested making a backup first.  It looks like the reconfigure also makes one for you.

Continue and see if it gives you a working file.

---

### Post by rkrug on 2007-06-29
> **nick_h said:**
> You can always select recovery mode from the grub menu if you really can't get to a terminal.

The command will overwrite /etc/X11/xorg.conf - that is why I suggested making a backup first.  It looks like the reconfigure also makes one for you.

Continue and see if it gives you a working file.

I can't continue, it exits the configuration after two steps and takes me to the command line.

---

### Post by nick_h on 2007-06-30
It should have modified your xorg.conf file.  Did you try to re-start X to test it?

If you are still having problems it may be worth you posting your xorg.conf and the errors you are getting.

---

### Post by rkrug on 2007-06-30
There is no text in my xorg.conf file

---

### Post by rkrug on 2007-06-30
hey I just got it working somehow, thanks!

---

### Post by rkrug on 2007-07-22
Okay, um this problem came back. :(

---

### Post by rkrug on 2007-07-22
nvm I just removed gdm and reinstalled it

---

