---
title: "Desktop background and cursor only."
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by Exciterusa on 2009-05-24
Maybe someone knows what's going on here. I got a new MSI nettop 100, put in a WD 1t green drive. Installed ubuntu 9.04 remix for atom. Install no problems.
Boot up no problems. Turn off maximize from startup programs and switch to classic desktop. Reboot. 
Now I get nothing but a desktop background and a mouse cursor after logging in. 
Tried reinstalling about 4 times now, same results. Doesn't matter if I grab all updates or do nothing else to the system before turning off maximize and classic.
First time I got all updates. Loaded firefox, had several reboots. It was fine.
Not sure if it's classic desktop or turning off maximize that breaks it. But the last install the only thing I did was first turn off maximize. Reboot, then switch to classic. Reboot, and then I'm stuck.

Help Please.

---

### Post by cody7002002 on 2009-05-24
I had this same problem but it was fixed after I reinstalled. Hopefully you'll get more help in this thread than I did in mine =/

---

### Post by Exciterusa on 2009-05-24
> **cody7002002 said:**
> I had this same problem but it was fixed after I reinstalled. Hopefully you'll get more help in this thread than I did in mine =/

Yeah, I'm kinda worried about that. Didn't find much help when I searched. Only solutions I found didn't apply.

---

### Post by samsunix on 2009-07-07
> **Exciterusa said:**
> Maybe someone knows what's going on here. I got a new MSI nettop 100, put in a WD 1t green drive. Installed ubuntu 9.04 remix for atom. Install no problems.
Boot up no problems. Turn off maximize from startup programs and switch to classic desktop. Reboot. 
Now I get nothing but a desktop background and a mouse cursor after logging in. 
Tried reinstalling about 4 times now, same results. Doesn't matter if I grab all updates or do nothing else to the system before turning off maximize and classic.
First time I got all updates. Loaded firefox, had several reboots. It was fine.
Not sure if it's classic desktop or turning off maximize that breaks it. But the last install the only thing I did was first turn off maximize. Reboot, then switch to classic. Reboot, and then I'm stuck.

Help Please.

I have same problem with mine asus eee 901 but only after I plug in my widescreen monitor(Acer AL2016W). I think these have something to do with virtual resolution...

- Samuli

---

### Post by samsunix on 2009-07-08
Problem solved:

[Bug](https://bugs.launchpad.net/desktop-switcher/+bug/349519): fast fix

Download [desktop switcher](http://launchpadlibrarian.net/26020903/desktop-switcher_0.4.6_i386.deb)  
then just:
```
sudo dpkg -i desktop-switcher_0.4.6_i386.deb
```

---

### Post by MianoSM on 2009-07-09
> **samsunix said:**
> Problem solved:

[Bug](https://bugs.launchpad.net/desktop-switcher/+bug/349519): fast fix

Download [desktop switcher](http://launchpadlibrarian.net/26020903/desktop-switcher_0.4.6_i386.deb)  
then just:
```
sudo dpkg -i desktop-switcher_0.4.6_i386.deb
```

Excellent link. I had fallen to making a launcher on my desktop by right clicking and pointing it at the NBR: /usr/bin/netbook-launcher

...I successfully installed the debian package, and still do not get the gnome panels, only the background and mouse. Highly aggravating to make it so far and get stymied by something so trivial. : (

---

