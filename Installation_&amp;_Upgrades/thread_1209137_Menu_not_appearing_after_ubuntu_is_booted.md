---
title: "Menu not appearing after ubuntu is booted"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by sinu_reddi@yahoo.co.in on 2009-07-09
Hi All,
 
I'm using ubuntu-9.04-desktop-i386 as guest OS in virtual box 3.0.0.
It has been working well with full screen untill i installed nvdia graphics on my host Win XP professional. After nvdia installation, ubuntu screen is only showing half of the entire screen. To solve this, i've installed VBoxLinuxAdditions and from then on started the main problem:
 
After booting and providing the login credentials, below are the messsage boxes i found:
 
1. User's $HOME/.dmrc file is being ignored. This prevents the default 
session and language being saved.File should be owned by user and have 
644 permissions. User's $HOME directory must be owned by user and not 
writable by others --- with a "OK" button
 
2. could not update ICEauthority file
home/srinivasa/.ICEauthority --- with a "close" button
 
3. There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256) --- with a "OK" button
 
I proceeded by clicking the buttons accordingly in the same order to find nothing but a plane screen with no menu/toolbar. Also, the half screen problem is not resolved.
 
I've no idea what to do thereafter..
 
 
Please help....
 
 
With Regards,
Srinivas

---

### Post by Peter09 on 2009-07-10
My guess is that virtualbox needs to be re-installed. When you installed the nvidia card you effectively changed the host configuration.

---

