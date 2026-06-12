---
title: "update problems on Ubuntu 5.10"
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by doconnor on 2006-02-15
When I log onto Ubuntu I have an icon on the top right that has Connection Properties: ETH0 that is running.

I am on Charter pipeline.  The download speed appears to be about 4M per hour.

I assume that this is some kind of auto update.
Is this what is running?  

Is there any way to speed up the download?  4M an hour is a mite slow.

Is there a way to know how big the total size of the file is?

Is there a way to get the updates 1 at a time?

How do you stop this?  I let it run overnight.  I finally just shut down.

I also notice after a while that there was another icon that said there were 10 updates available.

If you right click on it there are several options(show updates, install all updates, package manager, update package list now, show notifications, and preferences).  Show notifications had a checkmark.  I tried clicking on all of the others.  Nothing seemed to happen.  Some of them(maybe all) ask for a password.  I entered the password. The window went away and no new one appeared.

I checked system monitor.  Everything was sleeping except gnome-system-monitor which was running.

Memory used was 167.8M.  CPU useage varied from 4% to 30%.

I am new to Linux.

Thanks,

Dale

---

### Post by towsonu2003 on 2006-02-15
you can check out which programs are accessing internet, you can use ```
lsof -i -n
``` for programs running with your privileges and ```
sudo lsof -i -n
``` for all programs. Ignore the programs that mentions this ip: 127.0.0.1 You will do this from a terminal (Applications>Accessories>Terminal)

you can update your system with ```
sudo apt-get update
sudo apt-get upgrade
``` from the terminal again. You can also use synaptic (System>Administration>Synaptic Package Manager) to get updates one by one (Reload>Status>Upgradable-or something like that->choose the ones you want).

---

