---
title: "I need minimal Install NO GUI"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by chadk5utc on 2009-06-12
I want to install 9.04 onto a machine without an Install GUI or Gnome Desktop or any other. I have searched and found the majority of posts are quite the opposite. 
Not new to Ubuntu so let me have it,

      Thanks
          Chad

---

### Post by PureLoneWolf on 2009-06-12
The server edition doesn't install X by default if I recall.  What are you going to be using the box for?

---

### Post by chadk5utc on 2009-06-12
I will more than likely be using it as a server but need wireless card recognition that is defaulted into the desktop version. Tried once or twice to get wireless working in server, no luck. This is going to be a very remote solar powered machine.Weather Station/Video server on my farm.

---

### Post by xavierp94 on 2009-06-12
> **chadk5utc said:**
> I will more than likely be using it as a server but need wireless card recognition that is defaulted into the desktop version. Tried once or twice to get wireless working in server, no luck. This is going to be a very remote solar powered machine.Weather Station/Video server on my farm.
Try installing the desktop version of Ubuntu then remove the ubuntu-desktop package from Synaptic.

---

### Post by chadk5utc on 2009-06-12
ok that will work for one machine. Second machine is Ebox 2300 1Gb SSD 128ram and cf slot 3USB ports ?? this is the real challenge...

---

### Post by spcwingo on 2009-06-12
Why not use the mini ISO?  It just installs the Ubuntu base system (not server kernel) without the GUI.  The mini ISO can be found here:

[https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

If they don't have CD drives, but support USB booting just use unetbootin to create a bootable flash drive with the mini ISO image.  Just note that this will pull in everything from the repos, so an internet connection is mandatory for an install from the mini ISO.

---

### Post by chadk5utc on 2009-06-12
Thanks I didn't know there was a mini.iso , I will grab it and run it through Unetbootin and see if I can make it work.

---

