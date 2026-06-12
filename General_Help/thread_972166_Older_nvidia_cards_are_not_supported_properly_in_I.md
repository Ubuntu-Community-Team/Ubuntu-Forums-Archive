---
title: "Older nvidia cards are not supported properly in Intrepid???"
date: 2008-11-05
forum: General Help
---

### Post by peterdm on 2008-11-05
I have an older computer with an older nvidia video card. It still had desktop effects in Hardy, using the legacy (proprietary) nvidia glx driver. Before upgrading to Intrepid, I got a warning that my video card would not be supported anymore... It's great to get this warning upfront, but anyway, since I could not resist the urge to stay on the latest and greatest release, I upgraded anyway. I don't immediately need the 3D effects anyway.

However, I find it very unfortunate that this nvidia driver is not supported... I would really like to see proper support for these cards again in the future! Please please please!

Peter

---

### Post by Tamlynmac on 2008-11-05
Try this.

[http://http://albertomilone.com/wordpress/?p=294]("http://http//albertomilone.com/wordpress/?p=294")

---

### Post by peterdm on 2008-11-07
There's a typo in the above link, the correct one is

[http://albertomilone.com/wordpress/?p=294](http://albertomilone.com/wordpress/?p=294)

---

### Post by Tamlynmac on 2008-11-07
Sorry about the typo - don't know how it happened. Glad you figured it out.:smile:

---

### Post by peterdm on 2008-11-12
Added the proposed updates, pulled in all the updates, installed the restricted nvidia driver and it works like a charm.

Peter

---

### Post by kiran88pnjr on 2008-11-12
Hi,

I am currently using Intrepid in my nVidia 6150 SE card with 512 MB RAM. It works perfectly. Is that card so older ?:lol:

---

### Post by John Jason Jordan on 2008-11-13
> **kiran88pnjr said:**
> Hi,

I am currently using Intrepid in my nVidia 6150 SE card with 512 MB RAM. It works perfectly. Is that card so older ?:lol:

I have an nVidia 6150 also and after upgrading to Intrepid X would not start. I was dumped to a command line. This is on Intrepid x86_64.

By changing "nvidia" to "nv" in xorg.conf I am able to get a GUI, but it is stuck at 1050 x 768 (VESA). 

I want to reinstall the nvidia-glx-new driver, but apt-get says there is no longer such a creature. There also used to be a "restricted software" launch item under Administration, but I can't find it. In short, I can't find any way to install the nVidia driver short of Synaptic. And I can't use Synaptic because I can't figure out which driver to use for my 6150.

The 6150 (and my monitor) can do 1680 x 1050. That is what I had set up in Hardy using the nvidia-glx-new driver. How can I get this back after the upgrade to Intrepid?

---

### Post by kiran88pnjr on 2008-11-14
I have also upgraded to Intrepid from Hardy, but I haven,t got any problem.
Check this screen shot. Have u got restricted drivers in admin. menu ? If yes, Install that one or try to reinstall Intrepid.:lol:

---

### Post by John Jason Jordan on 2008-11-14
> **kiran88pnjr said:**
> I have also upgraded to Intrepid from Hardy, but I haven,t got any problem.
Check this screen shot. Have u got restricted drivers in admin. menu ? If yes, Install that one or try to reinstall Intrepid.:lol:

Well, since posting that things have gotten worse. At this point I can get the GUI at 800 x 600 and the mouse and keyboard are dead. In other words, I can't even log in, nor can I shell to a command line. All input devices fail to work.

If I boot to recovery mode there are various options. I booted in Recovery mode and then tried to repair X (accomplished nothing) and to repair components (also accomplished nothing). At the moment all I can get is the root command line by booting in Recovery mode.

Reinstalling will take about 20 hours of my time. Yes, it will take only an hour or so to reinstall, but then it will take 19 more hours to reinstall all my programs. 

However, I am pretty sure it will not be necessary to reinstall. I just need to figure out how to fix X manually. I think part of the problem is that the new X.org configuration takes the mouse and keyboard out of the xorg.conf file and puts them someplace else. Yet when I look at my xorg.conf file it still lists them. I need to do a lot of research to figure out how the new X.org works and how to get my video back the way it was.

---

