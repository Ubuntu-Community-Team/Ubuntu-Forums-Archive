---
title: "best desktop ubuntu for low-end hardware"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by bernardfrancois on 2007-05-19
I was wondering what's the best desktop ubuntu version for use on low-end computers, when software repository updates are not important.

I'm still using ubuntu 5.04 on a low-end laptop (pentium II 366mhz with 384mb ram), and I was wondering if I would get a performance boost by upgrading to a higher ubuntu version. I'm not talking about changing desktop managers or window systems, I'm talking about the default installs of ubuntu (not kubuntu, xubuntu, ...).

Does anyone know more about this or if there have been published test results of various ubuntu versions on low-end systems?

---

### Post by raja on 2007-05-19
I am not aware of any comparisons, but the general feel has been that edgy and Feisty have definitely been as fast as, and may even be faster than the older versions. 
My suggestion would be that you should upgrade to the latest. There definitely is not the windows-like phenomenon of newer  versions getting slower in Ubuntu.

---

### Post by aysiu on 2007-05-19
You won't get much speed benefit from staying with 5.04.

The best way to get a boost in performance is changing the apps you use and the window manager/desktop environment.

---

### Post by steve0921 on 2007-05-19
I am not sure about how processor speed is affected, but I have used several Ubuntu versions on computers with memory ranging from 200MB to 2GB. I have not seen any dramatic difference in performance between versions when using GNOME or KDE. No performance boost or detectable hit, though I suspect that resource usage is gradually increasing.

The only thing I have done that makes any appreciable difference, as aysiu indicated, is using xfce (or even better the command line if appropriate) instead of gnome or kde.

As for using 5.04 though, if the laptop you describe ever connects to the internet, you may want to consider upgrading to a supported distribution to obtain security fixes. I run Dapper (6.06 LTS) on an old desktop and a few light embedded systems with no problems.

---

### Post by ricrac on 2007-05-19
Xubuntu uses less system resources than Kubuntu or Ubuntu.

We use it for EMC cnc controllers.  
EMC comes distributed on Ubuntu.
Converting to Xubuntu and a little tuning allows it to run productively on Pentium III's.
It will not run without errors on the same machine as Ubuntu or Kubuntu with the same/equiv tuning.

It's easy in a desktop to fall back to Ubuntu performance from adding programs and their dependencies.  
The base Xubuntu includes includes variants of all standard desktop apps and a base desktop install of Xubuntu will use less resources than a base install of Ubuntu.
XFCE vs. Gnome

---

### Post by bernardfrancois on 2007-05-19
Ok, maybe I'll upgrade to the 6.06 LTS version...

I don't really like Xfce, but the last time I tried it was in fedora core 2... probably it got better.

However, most of the time I just use xterm, so I'll consider using a simpler window manager like twm.

---

### Post by kerry_s on 2007-05-19
You should go with a custom install so you can add only what you use.

-> [http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/mini.iso)

do a server install
login
sudo su
nano /etc/apt/sources.list <-uncomment all the repos, ctrl+x and y and enter to save.
apt-get update
apt-get install xorg gdm synaptic "your window manger of choice"
reboot
select your wm in session and login, open synaptic and continue to add what you need/want.

That is the best way to get a slim trim system built by you for you.

---

### Post by Ptero-4 on 2007-05-19
You may try xubuntu 7.04, it's lighter and newer than 5.04.

---

### Post by bernardfrancois on 2007-05-21
> **kerry_s said:**
> You should go with a custom install so you can add only what you use.
-> [http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/mini.iso)


I guess I can also do this with the standard ubuntu CD's, or am I wrong?

---

### Post by aysiu on 2007-05-21
> **bernardfrancois said:**
> I guess I can also do this with the standard ubuntu CD's, or am I wrong?
Yes, you can do it with a regular Alternate CD or Server CD--not with the Desktop CD, though.

More details here:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by Kobalt on 2007-05-21
K.Mandla also has amazing posts on [his blog]("http://kmandla.wordpress.com/") about such apps as rTorrent, cPlay, elinks... You might want to take a look at this to get really good and very light alternatives.

---

