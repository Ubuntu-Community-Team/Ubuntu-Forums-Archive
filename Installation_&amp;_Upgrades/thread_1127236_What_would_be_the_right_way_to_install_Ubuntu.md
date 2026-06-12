---
title: "What would be the right way to install Ubuntu?"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by willpower232 on 2009-04-16
I have been using Ubuntu since 2006 and am quite comfortable setting it up the way I want it.

Currently I only have Ubuntu servers so I always download the Server install CD and then install the Gnome desktop on top via aptitude.

Downloading the ubuntu-desktop package for this purpose is very time and bandwidth consuming because of everything else that gets downloaded and installed as well.

With Jaunty just around the corner, I am also looking to use a couple of Ubuntu desktops in combination with the servers.

So I was thinking that it might be simpler to download the Desktop install CD and then swap the kernel to the server version on the computers I want to be servers.

Ubuntuforums has gotten me out of a lot of holes before but I can only find mentions of the ability to swap kernels.

So can one of you bright sparks out there help out? Is there a better way of doing things or am I chasing one big pipe dream?

Thanking you muchly

---

### Post by StuartN on 2009-04-16
You could download everything you need to the server and then set the server as your proxy web server on the other machines, so at least all the bandwidth would be local from the server's package cache.

---

### Post by willpower232 on 2009-04-17
I could but I wouldn't have the foggiest idea how to do that. Also that would require a lot of messing around that I would probably undo when my install-fest was over.

Unless I'm mistaken of course?

---

### Post by StuartN on 2009-04-17
> **willpower232 said:**
> Also that would require a lot of messing around that I would probably undo when my install-fest was over.

Not at all. You simply need to install apt-proxy on the server that is intended to cache packages and set all the other machines to look at the server for any updates. Then every package will be downloaded and cached by the server just once. You can leave it in place for all package management so that regular updates are cached.

There is an Ubuntu tutorial here [https://help.ubuntu.com/community/AptProxy?action=show&redirect=AptProxyHowTo](https://help.ubuntu.com/community/AptProxy?action=show&redirect=AptProxyHowTo) and a Debian tutorial with more details here [http://www.debian-administration.org/articles/406](http://www.debian-administration.org/articles/406)

---

### Post by spcwingo on 2009-04-17
> **willpower232 said:**
> So I was thinking that it might be simpler to download the Desktop install CD and then swap the kernel to the server version on the computers I want to be servers.

I can confirm that this can be done.  I have Hardy installed on one of my machines and swapping out the kernels is as easy as any other software installation via synaptic.  Just search for "linux-image" and look for the latest kernel that ends in "server".  While in there also search for "modules" and look for "linux-restricted-modules" and "linux-ubuntu-modules" that correspond with the kernel version (and that end with "server").  After that reboot with the server kernel and uninstall the generic along with their corresponding modules.  After that you should be all set.

---

### Post by willpower232 on 2009-04-17
In retrospect, I think I'm going to follow both of these because the server that would an ideal (i.e. is always on) apt-proxy has limited hard drive space and I don't have the monies for more hard drives (yet).

Thanking you both muchly :D

---

### Post by StuartN on 2009-04-17
I am not certain, but I think there should be no increase in storage requirements on the server - all the debs that the server has downloaded are currently stored in /var/cache/apt/archives so you would simply be sharing them rather than duplicating them. (For guesstimating, this directory is currently 4.7 G on my system with no attempt at cleaning up). I guess if apt-proxy insists on a separate cache and duplicates this, then you would get an immediate 4.7 G hit, although it does have functions to purge old packages. apt-proxy and similar package cachers work great in school labs and similar settings.

---

### Post by willpower232 on 2009-04-17
so if i "apt-get autoclean"-ed every now and then, I should not worry at all?

Edit: I mean should I "apt-get clean" the clients, especially the apt-proxy server so that I don't have lots of duplicates existing in my network?

---

### Post by StuartN on 2009-04-17
Yes, the clients will continue exactly as before, only packages will download immediately if anyone has installed them. The server will need some cleaning if it runs out of space, and some cleaning can be automated in the apt-proxy settings.

---

### Post by willpower232 on 2009-04-17
Ah that makes sense.

Thanks very much Stuart.

All being well, I should be able to devote the entire weekend of the 25th and 26th to it so I have much Jaunty fun to look forward to.

---

### Post by willpower232 on 2009-04-25
I have just got apt-proxy working and I need to add one little bit of information for people who find this.

In the apt-proxy configuration file, the paths to the backends have to have a / at the end.

It doesn't say that on the wiki...but is apparently needed for jaunty to get the apt packages.

---

