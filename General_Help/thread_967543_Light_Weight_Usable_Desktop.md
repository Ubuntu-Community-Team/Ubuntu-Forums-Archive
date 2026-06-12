---
title: "Light Weight Usable Desktop"
date: 2008-11-02
forum: General Help
---

### Post by mashcaster on 2008-11-02
I would like to setup a light weight usable desktop as the standard setup is too much for my laptop.

I have already used the alternative cd to install a command line base system.  I would like to install LXDE and SLIM, but I don't want to install all the extras that come with LXDE.  Is it possible to install LXDE with some parameters to make it lighter?

And how do I install and setup SLIM to it automatically starts up and gots into LXDE when logged in?

---

### Post by ugm6hr on 2008-11-02
What extras does LXDE have that you don't want?

[http://packages.ubuntu.com/intrepid/lxde](http://packages.ubuntu.com/intrepid/lxde)

You can pick and choose which components you want (listed as dependencies), but there is probably little point in having a GUI desktop unless you include Openbox, panels, file manager at least (alongside necessary -common).

---

### Post by urukrama on 2008-11-02
If you don't like LXDE, you can install Openbox and whatever else you desire (panels, etc.). If you need help with configuring Openbox and so on, have a look at my Openbox guide (see my signature).

---

### Post by mashcaster on 2008-11-03
So far I have done a base command line install of ubuntu, followed by

aptitude install xorg
aptitude install --without-recommends lxde 
aptitude install slim

which has given me a basic desktop which is in total about 900Mb.  So basically I only have 100Mb left on my 1Gb HDD.  How do I streamline this further? When installing xorg, it installed a lot of stuff which I don't think I needed, I have an ati graphics card and it installed lots of stuff for other graphics cards for example.

---

