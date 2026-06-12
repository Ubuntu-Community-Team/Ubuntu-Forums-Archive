---
title: "Xubuntu slow on my Dell Latitude 600"
date: 2008-12-03
forum: Hardware
---

### Post by HitRefresh on 2008-12-03
Hello,

With some help on this forum, I managed to do a complete install of Xubuntu (8.10) on a Dell Latitude D600 (Pentium M 1GHz, 1GB RAM). I'm not sure why, but it seems to be a bit slow in terms of responsiveness of user interaction of menus, bringing up apps, and stuff like that. This laptop previously had WinXP, but I formatted and installed Xubuntu, mostly for speed, and I'm not seeing that. It seems to be a bit slower actually ? Is it the M processor ? ... Should I try regular Ubuntu ? Is there something that could be making it slow ? .. (really don't want to go back to XP)


Thanks,
-Bhav

---

### Post by kerry_s on 2008-12-03
first i'd check if your running at full speed and the cpu was recognized right:
in terminal:
**cat /proc/cpuinfo**

running a desktop is always going to be slower than it can be, there's a lot running behind it. to get real speed you can feel, you want to use a window manager and light programs.

you can add a wm to your current setup so you can get use to it, but the best way to go is a custom setup built from a base install up.

i use debian, so i'm not really sure whats in the ubuntu repo's, but here is what you should try. look in synaptic, select one of these:

lxde <most of the work is done just use it
fluxbox <these 3 require further setup
icewm
jwm

once you have 1 installed log out and select it in the log in manager menu and log back in.

---

### Post by gabril on 2008-12-04
its not the fastest of computers! I think its your hdd thats slow... i would recomend a lighter dist. but no linux will be as fast as the nt hybrid kernel in this case! XP IS your best choice here... otherwise try debian with fluxbox or icevm... or whatever!

---

### Post by HitRefresh on 2008-12-04
Yes, I understand it is not par with the latest machines, but I think 1GHz & 1GB ram is sufficient to run most linux distros comfortably. .. I'll try out what kerry_s stated and see what happens.

---

### Post by snowpine on 2008-12-04
Another vote for LXDE, I find it to be really user friendly and speedy. Simply open a terminal and:

```
sudo apt-get install lxde
```

Then, log out, select Options->Sessions->LXDE from the login screen.

I've had good luck with Ubuntu+LXDE on my 600mhz, 256mb Dell Latitude, so I'm sure it will work on yours. :)

---

### Post by kerry_s on 2008-12-04
> **HitRefresh said:**
> Yes, I understand it is not par with the latest machines, but I think 1GHz & 1GB ram is sufficient to run most linux distros comfortably. .. I'll try out what kerry_s stated and see what happens.

it's better than mine, i'm using a 10year old vaio laptop 450mhz 256mb ram. i use a custom debian lenny install, with jwm as my window manager.

---

### Post by Wiebelhaus on 2008-12-04
> **snowpine said:**
> Another vote for LXDE, I find it to be really user friendly and speedy. Simply open a terminal and:

```
sudo apt-get install lxde
```

Then, log out, select Options->Sessions->LXDE from the login screen.

I've had good luck with Ubuntu+LXDE on my 600mhz, 256mb Dell Latitude, so I'm sure it will work on yours. :)

Also 

[http://u-lite.org](http://u-lite.org)

---

### Post by HitRefresh on 2008-12-05
It sounds like lxde is what I need. I'm not interested cool desktop effects or eye candy, just need something fast to run applications and do some work. 

.. on a related note: Could I upgrade my Xubuntu to Ubuntu without doing a complete re-install ? If so, how... ?

---

### Post by snowpine on 2008-12-05
> **HitRefresh said:**
> It sounds like lxde is what I need. I'm not interested cool desktop effects or eye candy, just need something fast to run applications and do some work. 

.. on a related note: Could I upgrade my Xubuntu to Ubuntu without doing a complete re-install ? If so, how... ?

The "Remove Xubuntu" command on this page will "upgrade" you to the Gnome version of Ubuntu, just copy & paste into the terminal.

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by kerry_s on 2008-12-05
> **HitRefresh said:**
> It sounds like lxde is what I need. I'm not interested cool desktop effects or eye candy, just need something fast to run applications and do some work. 

.. on a related note: Could I upgrade my Xubuntu to Ubuntu without doing a complete re-install ? If so, how... ?

just install lxde, then log out & select it:
sudo apt-get install lxde

as for removing xubuntu, there's no easy way "xubuntu-desktop" is just a meta-package, i would just go into synaptic and remove whatever you don't want.

> Could I upgrade my Xubuntu to Ubuntu without doing a complete re-install ?

the ubuntu desktop with gnome is "ubuntu-desktop", that meta-package will install all the things for ubuntu.

---

### Post by HitRefresh on 2008-12-10
Thanks for the help. Using lxde is faster, I'm going to try out ubuntu+lxde soon.

---

