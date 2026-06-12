---
title: "Nvidia 9500GT Install problems"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by akrobert on 2009-09-06
Hello
I just installed an Nvidia 9500GT Graphics card in the PCI Express slot. I have it up and running on my primary screen but cannot get the second screen on unless I use Truview which I dont like.

When I try to set it up as a seperate X Screen it gives me the following error.

> The current settings cannot be completely applied due to one or more of the following reasons

The Location of an X screen has changed
The location type of an x screen has changed
the color depth of an x screen has changed
An x screen has been added or removed
Xinerama is being enabled/disabled

For all the requested settings to take effect, you must save the configuration to the x config file and restart the x server.

I have an apply what is possible and a cancel

If I hit apply whats possible it does nothing. If I try to hit save to x configuration file it says

> 
Unable to create new X config backup file '/etc/X11/Xorg.config.backup'

I have a Dell 530 that I purchased preloaded with Ubuntu 8.04
Im running Ubuntu 9.04 now. Kernel 2.6.28-15 and Gnome 2.26.1

I have tried enabling the proprietary drivers and installed the nvidia drivers via the Synaptic package manager. 

What do I need to do to get the second monitor up and running?

thanks for the help

Robert

---

