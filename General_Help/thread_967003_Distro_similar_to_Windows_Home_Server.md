---
title: "Distro similar to Windows Home Server?"
date: 2008-11-01
forum: General Help
---

### Post by WVSteelers28 on 2008-11-01
Hi all.

I've an older computer that I would like to turn into a small home server.  I've downloaded and install Ubuntu 8.04 Server Edition because one, I wanted to mess around a little with some of the stuff and two, why not try new things. 

Unfortunately, I don't have the best skills when it comes to doing stuff by command line.  I'm wondering if there is a distro out there that is similar to Windows Home Server?  Something that is simple to install and configure, and has a lightweight GUI.  

I'm going to keep looking, but thanks.

WVSteelers28

---

### Post by rhcm123 on 2008-11-01
It's all text based, but you can get the gui (assuming your computer supports it) by typing this command.
```
sudo aptitude install x-window-system-core gnome-core
```
then
```
sudo aptitude install gdm
```
reboot and you shall have the standard ubuntu GUI!

I also suggest the following (google them)
for gui config:
webmin
ssh (use it on a gui-based computer, ssh to the server and admin via that)

Most text-based editing is not that hard. I've been doing it for a couple months now. You get used to it. GUI's are a bit overrated.

---

### Post by rhcm123 on 2008-11-01
Although i will warn you, x server and x desktop is considered a security risk. YOU HAVE BEEN FORWARNED!
(Might i suggest firestarter?)

---

