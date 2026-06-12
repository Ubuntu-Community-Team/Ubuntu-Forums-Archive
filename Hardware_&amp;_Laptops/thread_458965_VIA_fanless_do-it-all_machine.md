---
title: "VIA fanless do-it-all machine?"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by amkrisis on 2007-05-30
Hi

I'm thinking of setting up a small server and was wondering if i can pull the folowing off...

I'm thinking of making a fanless (or quiet) system.
It has to be small in size, so those VIA Mini-ITX boards came to mind. These boards pack some low end cpu's however (around 1ghz)

I basicly want to use it as:

- Media playback device (trough s-video out), no recording, no watching tv, just playback
- MLDonkey (or other) downloading (Bitorrent)
- LAMP webserver (only for the webgui of MLdonkey)

I'll also be running Gnome, since I like to configure things in there.

Can this be done on a machine like stated above?

Also, for media playback I though using a software like Freevo or Mythtv. Are there any wireless keyboards around that have a mouse (or trackball) in them, that work straight out of the box (so i can use them to install and configure the computer aswell)

---

### Post by AnRa on 2007-05-30
For the webserver you may use [Lighttpd](http://www.lighttpd.net/). :)

---

### Post by doogy2004 on 2007-05-30
Yes, i'm running a server on a 400 mhz celeron with onboard graphics.  I ran vmware with 2 vms running on it as well as a webserver and file server and print server.  I KNOW that you will be fine.  I'm also working on the exact same thing for my media center over the summer.  My recomendation would be to use the server CD and install a LAMP server once the LAMP is installed then do and apt-get install ubuntu-desktop.  Then  get Automatix at [http://www.getautomatix.com](http://www.getautomatix.com)  to help you install other software for media playback.

---

### Post by tturrisi on 2007-05-30
apt-get install ubuntu-desktop will give your server the full bloated ubuntu gnome setup, which you don't need.  All you need is a simple gui, thus better off installing Etch & gnome-core xorg if you want gnome.

---

### Post by kerry_s on 2007-05-30
for the system-> [http://www.damnsmalllinux.org/store/Mini_ITX_Systems](http://www.damnsmalllinux.org/store/Mini_ITX_Systems)

for the distro-> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-netinst.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-netinst.iso)

---

