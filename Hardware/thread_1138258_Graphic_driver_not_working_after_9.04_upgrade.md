---
title: "Graphic driver not working after 9.04 upgrade"
date: 2009-04-26
forum: Hardware
---

### Post by joe2me on 2009-04-26
I upgraded to 9.04 and after that my graphic driver stopped working and I'm forced to run low-graph mode until I can fix this:/

The error I get when I start the computer is:
(EE)NVIDIA(0): failed to load the nvidia kernel module!
(EE)NVIDIA(0): *** ABORTING ***
(EE) Screen(s) found, but none have a usable configuration.

It seems like all I need to do is activate the propriety driver but when I try it just says 0% for a short while and then disappears without doing anything.

Any ideas how to fix the graphic or any other info I should post?

---

### Post by joe2me on 2009-04-26
what else can I post to get help?

---

### Post by doas777 on 2009-04-26
first, open a terminal by pressing Ctrl + Alt + F1.
login, and run:
```

sudo gdm stop

``` 

then enter:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

then after it is done, try to start x again with:
```

startx

```

---

### Post by joe2me on 2009-04-27
doesn't seem to help:/

**sudo gdm stop**
```
gdm[3468]: WARNING: GDM already running. Aborting! 
WARNING: GDM already running. Aborting!
```
[B]
sudo dpkg-reconfigure -phigh xserver-xorg[/B]
```
xserver-xorg postinst warning: overwriting possibly-customised configuration file; 
backup in /etc/x11/xorg.conf.20090427201227
```

**startx**
```
Fatal server error: server is already active for display 0. 
If this server is no longer running, remove /temp/.XO-lock and start again
```

---

### Post by Almighty on 2009-04-27
Have you tried to install the nvidia driver from the restricted driver app built into ubuntu?

---

### Post by joe2me on 2009-04-27
if by that you mean the "Hardware drivers" tool for configuring third party and propriety drivers then yes. Also tried the EnvyNG without success:/

---

### Post by joe2me on 2009-04-28
*bump*

anyone?!

---

### Post by Almighty on 2009-04-29
What errors messages are being displayed?

---

### Post by joe2me on 2009-04-29
> **Almighty said:**
> What errors messages are being displayed?

Apart from the ones posted in my previous responses?!

---

### Post by kaltv on 2009-04-30
*Phew* That was a tough one!

Here's what I did:
1. Applications -> Add/Remove
2. type "nvidia" in search. Look! Drivers! Just pick one, it doesn't have to be the latest one. It said my hardward isn't compatible with the 177 one (I couldn't even Find the 180 one), so I picked the 173 one.
3. Once it's done installing, Then you go System -> Admin -> Hardware Drivers

Select the one you manually installed, then everything will hopefully work after that. Hopefully.

---

### Post by K. Hendrik on 2009-04-30
You could also try the drivers from the [NVIDIA download page]("http://www.nvidia.de/Download/index.aspx?lang=en")

open a terminal with Ctrl + Alt + F1 and execute the following

```

sudo /etc/init.d/gdm stop

sudo sh *here input the path to the driver you downloaded*

sudo /etc/init.d/gdm start

```

---

### Post by Mad dog on 2009-04-30
Hey guys!

I'm having the same exact problem, I install the driver, but when I try to activate it, nothing happens! Is there some way to manually activate it?

---

### Post by fletchoid on 2009-05-01
This upgrade seems to be causing a lot of problems with the proprietary drivers and X.
see [https://bugs.launchpad.net/ubuntu/+bug/366529](https://bugs.launchpad.net/ubuntu/+bug/366529) for my own nightmare.
I have been reading a lot of posts where both ATI and Nvidia drivers break the system, and Xorg breaks, and there is no sound, etc. etc.  Geez, this is almost like a Microsoft release!  Well, except that it was free, and there is a helpful community to help fix the problems, and the Ubuntu organization doesn't lie and pretend that everything is okay and its just the stupid user that needs to buy a new computer and new software.  Come to think of it, it isn't anything like a Microsoft release... what was I thinking?

---

### Post by joe2me on 2009-05-03
I solved my problem by saving my files and then re-installing 9.04 from scratch...

---

