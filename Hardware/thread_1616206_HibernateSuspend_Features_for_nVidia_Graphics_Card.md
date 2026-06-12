---
title: "Hibernate/Suspend Features for nVidia Graphics Cards?"
date: 2010-11-07
forum: Hardware
---

### Post by mlupton on 2010-11-07
I'm currently running Ubuntu 10.10 Maverick Meerkat on my Asus N82. I remember reading somewhere that the Hibernate and Suspend features are not supported by Ubuntu for laptops with nVidia graphics cards. My graphics card is an nVidia GEFORCE GT 335M. Is there anyway to enable these features, or will they ever be supported? The nVidia Xorg Settings has nothing to enable/disable Hibernate and Suspend, so I'm kind of at a loss. If there is any kind of workaround for this please post to this thread.

---

### Post by Xehoz on 2010-11-23
There's an issue with USB 3.0 and it's module and hibernation/suspension.

Check [this post]("http://ubuntuforums.org/showpost.php?p=9180298&postcount=7") to find out how to disable USB 3.0 for that purpose.

I had it sort of working on an Asus N82JV (I honestly don't remember exactly to what degree) a few months ago, but then I decided to reinstall my distro (Arch Linux) and haven't bothered to try to set it up again. Until now that is. I'll check back in if I do succeed.

Anyway, there really isn't a problem with the nvidia card and suspension/hibernation (like I said, I had it working). Nevertheless, you might want to check 
the [wiki page I wrote a few months ago on Arch Linux's Wiki about my Asus N82JV]("https://wiki.archlinux.org/index.php/Asus_N82JV"). It has a chapter about disabling the nvidia card, mostly because of the power it uses, despite not actually working if the Intel one is set up on Xorg, to the best of my knowledge. Keep in mind though, that the described steps may or may not require some adaptation to Ubuntu's reality.

---

### Post by Xehoz on 2010-11-26
Solution:

1. Open up the console and create a new file:
```
sudo nano /etc/pm/config.d/usb3-suspend-workaround
```

2. Add this line:
```
SUSPEND_MODULES="xhci-hcd ehci-hcd"
```

That's it. 

Suspend to Ram works by:
a) Typing *sudo pm-suspend* in the console;
b) Ordering to suspend in KDE menu (I figure, Gnome menu should behave/call the same thing);
c) Pressing keys Fn+F1.

---

### Post by mlupton on 2010-12-07
Thanks so much for the support, but does the workaround for USB 3.0 diminish the read/write speed offered by that port (thus, rendering it to be effectively USB 2.0)?
By the way, I would like to say that the advice offered has been extremely helpful, the nVidia proprietary graphics driver says absolutely nothing about what to do in this situation

---

### Post by knatten on 2010-12-25
Thanks Xehoz, the /etc/pm/config.d/usb3-suspend-workaround solution worked on my HP EliteBook 8740w.

---

### Post by mlupton on 2011-01-14
I'm sorry I forgot to thank you earlier xehoz, but that worked for me too. The only strange thing is that for some reason suspend features don't work, yet hibernate does fine. Wonder why...

---

