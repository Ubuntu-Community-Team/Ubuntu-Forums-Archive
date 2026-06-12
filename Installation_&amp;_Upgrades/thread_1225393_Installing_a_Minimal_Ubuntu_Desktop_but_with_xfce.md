---
title: "Installing a Minimal Ubuntu Desktop but with xfce"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by user 123 on 2009-07-28
I found this thread a while ago about installing a minimal Ubuntu desktop by using a minimal or server installation and then using command line to install a few packages to get a useable desktop:

[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

I was wondering what changes i would need to make to use xfce instead of Gnome? A kind of minimal version of the now bloated Xubuntu which is still not lightweigh enough for my liking. If anyone could alter the code and repost it for xfce, or just tell me what packages would need to be changed, I'd be very grateful. Thanks in advance!

---

### Post by user 123 on 2009-07-28
For those who can't be bothered to go to the thread with the code here it is:

```
#!/bin/bash
#######################################################################
# Ubuntu-Desktop-Minimal: Post-install script to install only the bare
#			  essentials of an Ubuntu Desktop.
#######################################################################
echo "[*] Installing Gnome Essentials"
sudo apt-get -y install gnome-core gdm network-manager-gnome fast-user-switch-applet \
human-theme x11-xserver-utils tangerine-icon-theme gnome-themes-ubuntu ubuntu-artwork \
jockey-gtk gnome-screensaver gnome-utils
echo "[*] Installing Application Essentials"
sudo apt-get install -y gcalctool tsclient
```


Alternatively a list of just the basic apps needed for a bare xfce desktop in Ubuntu would be nice :)

---

### Post by mikewhatever on 2009-07-28
sudo apt-get install gdm xorg xfce4

That will get you the login manager and the GUI. Add programs later as needed.

---

### Post by user 123 on 2009-07-28
> **mikewhatever said:**
> sudo apt-get install gdm xfce4

That will get you the login manager and the GUI. Add programs later as needed.

Thanks, I will try this asap!

---

### Post by mikewhatever on 2009-07-28
> **user 123 said:**
> Thanks, I will try this asap!

I've missed xorg, adding it to the previous post. Can you elaborate what you want the system for. Is it just to have a gui on the server, or are you going to use it as a desktop? Is it a laptop?

---

### Post by user 123 on 2009-07-28
> **mikewhatever said:**
> I've missed xorg, adding it to the previous post. Can you elaborate what you want the system for. Is it just to have a gui on the server, or are you going to use it as a desktop? Is it a laptop?

It's for a desktop with low specs. The standard Xubuntu installation is too bloated for my liking but I like the interface, so I want to start with a bare bones installation and work my way up installing just the things I need.

---

### Post by mikewhatever on 2009-07-28
> **user 123 said:**
> It's for a desktop with low specs. The standard Xubuntu installation is too bloated for my liking but I like the interface, so I want to start with a bare bones installation and work my way up installing just the things I need.

Excellent idea. I've been running a minimal installation with LXDE, and love it.

---

### Post by user 123 on 2009-07-28
> **mikewhatever said:**
> Excellent idea. I've been running a minimal installation with LXDE, and love it.

Sounds good, how does LDXE compare with xfce?

---

### Post by user 123 on 2009-07-28
If i wanted to install LXDE instead of XFCE would I just change 
sudo apt-get install gdm xorg xfce4
to
sudo apt-get install gdm xorg lxde

?

---

### Post by mikewhatever on 2009-07-28
It's also a lightweight environment with OpenBox window manager and pcmanfm file manager. In comparison, XFCE has xfwm and thunar. It looks like XFCE has a lot more packages and goodies to choose from.

---

### Post by bkusa on 2009-07-28
also you could just try using crunchbang (#!) which is a VERY lightweight ubuntu variant that uses openbox and a few very lightweight programs.

---

### Post by user 123 on 2009-08-04
> **mikewhatever said:**
> I've missed xorg, adding it to the previous post. Can you elaborate what you want the system for. Is it just to have a gui on the server, or are you going to use it as a desktop? Is it a laptop?

Would the packages need to change at all if it were for a laptop?
I'm enjoying the lightweight XFCE so much I've decided I'm going to install it on my laptop too.

---

### Post by user 123 on 2009-08-04
Basically, will I experience any problems, loss of functionality etc using these as base packages on a laptop? I will probably install xfce power manager anyway.

---

### Post by scales on 2009-08-05
the best minimal xfce4 ubuntu i could find was [http://distrowatch.com/weekly.php?is...090504#feature](http://distrowatch.com/weekly.php?is...090504#feature)

not bad but i dont think it installs much of the basic things like archiver, picture viewer, screensaver, etc. anyone have advice on this?

---

### Post by Ozitraveller on 2009-08-05
I did 2 posts here that might help:
[http://ubuntuforums.org/showthread.php?t=1155961&page=8](http://ubuntuforums.org/showthread.php?t=1155961&page=8)
[http://ubuntuforums.org/showthread.php?t=1155961&page=6](http://ubuntuforums.org/showthread.php?t=1155961&page=6)

---

