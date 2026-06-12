---
title: "How to configure Nvidia for X11?"
date: 2023-11-13
forum: Hardware
---

### Post by bcld-man on 2023-11-13
[FONT=arial][COLOR=#161616][B]Use case
[/B]I am trying to find a way to support Nvidia drivers (535) on a Linux bootable RAMdisk. 
I have created a Linux distribution from scratch, based on a Jammy bootstrap.
The purpose of this light Linux distro is to execute applications inside a kiosk environment. 
Some applications require high performance graphics.

Most existing distros use Nouveau drivers in their public images, but these perform extremely poorly on newer RTX cards. 
Nvidia drivers are openly available in Ubuntu and some of my clients use RTX cards. 
So I tried making a bootable ISO that has these available Nvidia drivers.
The problem is that my project runs on X11 and nvidia-xconfig does not do anything nor does nvidia-xrun or nvidia-settings. 
I know that nvidia-xconfig is outdated, and I cannot find out how to use nvidia-settings with our configurations. 
nvidia-xrun seems to turn the screen off just like startx.

[B]The problem
[/B]This brings me to my question: Is it permitted and possible to ship a Linux bootable ISO with Nvidia drivers provided by open source repositories?
If not, how else can I support newer RTX cards in my image? Nouveau drivers are very inefficient.
If so, how do I make X11 run properly without the need to reboot? 

**Current situation**
My process has been running through X.org.log files until my EErors and WWarnings are gone.
Since I work from scratch, I do not have a session or display manager like LightDM or GDM. 
I run applications with X11 through Openbox and custom Xsettings. 
I have managed to fix the ModulePaths and get most of the modules loading, though I am not able to see anything after using startx or nvidia-xrun, meaning I cannot run an xrandr --auto.

I could supply X11 configs or logs if necessary.[/COLOR][/FONT]

---

### Post by TheFu on 2023-11-13
These nvidia questions require a lawyer and discussions with nvidia legal.  Nobody here works for Canonical.

---

