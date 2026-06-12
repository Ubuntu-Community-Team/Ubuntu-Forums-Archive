---
title: "Some troubles with ASUS GeForse 570"
date: 2011-11-04
forum: Hardware
---

### Post by fatal_ERROR777 on 2011-11-04
Hello!
I've got a new PC last week with nothing installed on it. The characteristics are blowing: over 4 GiB of ram, over 4 CPUs, etc... With a little BUT.

The annoying video card doesn't want to work. I've tried everything I could: installed the dev versions of this driver, using the Nvidia Driver from the official website. I've installed ubuntu 11.10 64-bit.

So the problem is: Many games which require a video acceleration (like minecraft) doesn't work at all, they give crash messages :(

Probably the solution: Installing some drivers
After doing so, My Unity 3D session load the desktop only, without a launcher, and any other stuff, I open up tty1 and reload the X-server (lightdm)

After this "solution" minecraft works, but Unity 3D doesn't

The driver which is installed right now can be found [here ]("http://www.geforce.com/Drivers/Results/38743")

any suggestions?

~fatal_error

---

### Post by fatal_ERROR777 on 2011-11-06
Ok, got it.
There are no stable versions of Nvidia drivers released for ubuntu 11.10 amd64 by the ubuntu community. There is some kind of drivers made by xorg-pushers and nvidia, but they are laggy and unstable. I'll mark it solved. 

The solution is: install the LTS version (10.04). For more modern look and feel, try messing up with gnome-3, though it's not recommended for new ubuntu users, because you won't have a big support from ubuntu developers, because they are planning to include gnome3 in version 12.04 (I guess)... If you really want to try out gnome-3, install Fedora or OpenSuse.

~fatal_error

---

