---
title: "New ATI drivers"
date: 2005-02-17
forum: Hardware &amp; Laptops
---

### Post by ember on 2005-02-17
So actually just a few hours ago, ATI released a new driver package, Debian packages available at:

[http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html)

The good thing: It might fix some issues for some people
The bad thing: It still doesn't support my &%$**§$$ Sapphire card ... think I'll go for Nvidia next months

In need for weapons of mass destruction,
ember

---

### Post by sunscape on 2005-02-17
Any chance it will be added to the repositories... like tomorrow?  :shock:

---

### Post by dewey on 2005-02-17
Do they even put ATI drivers in the repos in the first place?

I haven't seen any for 3d support.

I'll try and install the drivers now.

---

### Post by sunscape on 2005-02-18
I believe you are correct about not supporting 3D. I have a radeon 9600.

It really sucks since I don't want to mess with the drivers from the ati web site. I simply do not want to fud my setup now that I have everything working (at last). 

Could you post your results of the new driver install? I might become brave enough to try an install.

---

### Post by sard on 2005-02-18
[QUOTE=sunscape]I simply do not want to fud my setup now that I have everything working (at last). [/QUOTE]

I know what you mean, I've spent ages setting everything up just how I want it, but my desktop is soooo sluggish at the moment which is ridiculous as I have a 9700pro. I get 300 whole fps in glxgears  :lol:

---

### Post by daniels on 2005-02-18
Uh, xorg-driver-fglrx has been in there since the day they released 8.8.25.  Unfortunately, we're now in an upstream version freeze, so the new drivers (8.10.19, I think -- I watch the atilinuxbeta list) probably won't go in.

---

### Post by sunscape on 2005-02-18
I guess if 8.10.19 doesn't support 3D for my card (9600) then it doesn't really matter since I have been using the current driver in the repositories. But that is a crying shame for everyone that uses an ati card because the current drivers need as much improvement as possible.

---

### Post by ember on 2005-02-18
If you have a standard ATI 9600 I guess it will work. It only doesn't work on mine because it seems Sapphire used a Radeon 9600 Mobility, yet incremented the vendor ID by one. Thus it is not known by the kernel module and therefore not supported.
You may check the support for your card by looking it up in the list on the page I mentioned in my first post.

---

### Post by dewey on 2005-02-18
Not going too well, I'm up to making my packages, so I can modprobe fglrx, but I can't seem to find my kernel sources.  I'm pretty new to setting up linux drivers like this, getting down and dirty with sources isn't one of my best strengths.  I'm using the k7 kernel from backport I believe.
"linux-k7 2.6.8.1-15"

Any help is appreciated, so I can figure out if these drivers actually work, or they blow up your computer. :)

[edit:] There seems to be a package called "linux-source 2.6.8.1" I wonder if that's what I have to install, then point to it's dir... But it's not the exact same as my current kernel "linux-k7 2.6.8.1-15"  So I'm not sure if it's right. [/edit]

---

