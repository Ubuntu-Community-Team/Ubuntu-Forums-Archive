---
title: "Trackpad multi touch causes cursor to jump - can't find 11-x11-synaptics.fdi"
date: 2010-11-29
forum: Hardware
---

### Post by krunalpatel on 2010-11-29
Trying to get my multi touch trackpad to work. I have a Dell XPS 15 (L501x). It sees that I have a Synaptics Trackapd. I've searched and searched for a soulution to turn on 2 finger scrolling - but all the guides direct me to :

> sudo cp /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi /etc/hal/fdi/policy/
gksudo gedit /etc/hal/fdi/policy/11-x11-synaptics.fdi

I can't seem to find that file. It's not in that folder. When I tried to create the file and paste the info and save it... my ubuntu wouldn't boot into gnome after I rebooted. 

I'm running 10.10 Maverick

---

### Post by krunalpatel on 2010-11-30
bump

---

### Post by Jophish on 2010-11-30
Hi

I had multitouch working with this laptop. But I messed things up while fiddling about with xorg.conf. I'm unable to get back to a state where things are working. But I know that this is possible to do, or I was just dreaming it all...

---

### Post by krunalpatel on 2010-11-30
> **Jophish said:**
> Hi

I had multitouch working with this laptop. But I messed things up while fiddling about with xorg.conf. I'm unable to get back to a state where things are working. But I know that this is possible to do, or I was just dreaming it all...

You had it working by default or did you do some custom mods? What version of ubuntu are you running?

---

### Post by Jophish on 2010-12-07
Hi

[This]("http://ubuntuforums.org/showthread.php?t=1435663")
Sorted things for me. It seems as though you can set most of the properties for the Synaptics driver with this.

Good luck.

Joe.

---

