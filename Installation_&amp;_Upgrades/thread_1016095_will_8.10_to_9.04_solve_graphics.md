---
title: "will 8.10 to 9.04 solve graphics?"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by jesse c on 2008-12-19
I still,after 1 1/2 months now,am working in low graphics mode because i cant get my new nvidia 9400gt graphics card to be recognized by ibex 8.10.I now see that an update to 9.04,Jaunty i assume,is available.Jaunty has the newest 180.11 nvidia driver in its synaptic package.Since Ibex didnt work do i have anythihg to lose by upgrading to 9.04 and seeing what else is availabile as far as nvidia in there synaptic packages?

---

### Post by oilchangeguy on 2008-12-19
> **jesse c said:**
> I still,after 1 1/2 months now,am working in low graphics mode because i cant get my new nvidia 9400gt graphics card to be recognized by ibex 8.10.I now see that an update to 9.04,Jaunty i assume,is available.Jaunty has the newest 180.11 nvidia driver in its synaptic package.Since Ibex didnt work do i have anythihg to lose by upgrading to 9.04 and seeing what else is availabile as far as nvidia in there synaptic packages?

9.04 is still in alpha. i'd stay far, far away from software still in development.

---

### Post by Sealbhach on 2008-12-19
It would not be wise to upgrade to Jaunty, but you can temporarily enable the Jaunty repo to download 180.11. It worked fine for me but you need to be careful to undo the changes in Software Sources or you could really mess up your system.

See here for how to do it:

[http://ubuntuforums.org/showthread.php?t=1002828](http://ubuntuforums.org/showthread.php?t=1002828)

Careful!:p

.

---

### Post by jesse c on 2008-12-19
Thanks Sealbhatch. I followed the link and did the jaunty 180 package and removed jaunty as per instructions.Now i have the 180 driver checked green in my Intrepid synaptic list but my system still does not recognize that i have nvidia installed.Restricted driver manager says that no restricted drivers are in use on my system.

---

### Post by Sealbhach on 2008-12-19
That's normal. Install nvidia-settings. This will show up in your System/Administration menu. Go into it and see what driver it sees.


.

---

### Post by jesse c on 2008-12-19
Sealbhach- nvidia settings are checked in synaptic but its version 178.xxx not 180  and sys/admi/nvid settings says there is no nvidia being used and no x server running

---

### Post by Sealbhach on 2008-12-19
Ok, try this. Log out and at the login screen, press <Ctrl><Alt>F2 to get to a console. Log in and shutdown gdm with


```

sudo /etc/init.d/gdm stop
```

Now, type 

```
sudo dpkg-reconfigure xserver-xorg
```

This should get xorg configured for the new driver.

Then restart the GUI:

```
sudo /etc/init.d/gdm start
```

If that doesn't work, repeat but use the command

```
sudo nvidia-xconfig
```

instead.


.

---

