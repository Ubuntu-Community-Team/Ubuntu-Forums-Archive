---
title: "Installing wlan card breaks sudo command"
date: 2005-11-04
forum: General Help
---

### Post by pawdk on 2005-11-04
Hiya,

I'm rather pleased with Ubuntu. I've done several installs in the last few weeks, testing out and breaking Ubuntu over and over again... Guess it's in my nature :)

I have a problem with my wlan now though, it's something that I've seen happen before...

**Problem:** When I install Ubuntu, my ASUS (marvell chipset) wlan card isn't recognized, and I have to install it myself. I do so using ndiswrapper, and then using 'modprobe ndiswrapper' to get it to show up in the admin network tool, where I enter the IP and DNS info. And voila, it works.

But... Now I can't use the sudo command anymore :???:  and I haven't the slightest idea why installing my wlan card should break the sudo command... Whenever I try to use sudo, nothing happens. It just does nothing...

Does anyone have any idea why this is happening?

In advance, thanks...

(PS: can't seem to find the post detailing how you made Ubuntu do the ndiswrap command automatically at each startup, does anyone remember?)

---

### Post by mlomker on 2005-11-04
> (PS: can't seem to find the post detailing how you made Ubuntu do the ndiswrap command automatically at each startup, does anyone remember?)

Just add ndiswrapper to the end of the /etc/modules file.

I'm not sure what you mean by 'nothing' with the sudo command.  Are you saying that you type **sudo synaptic** in a terminal and it returns you to the line with nothing occuring?  Have you looked at /var/log/auth.log?

---

