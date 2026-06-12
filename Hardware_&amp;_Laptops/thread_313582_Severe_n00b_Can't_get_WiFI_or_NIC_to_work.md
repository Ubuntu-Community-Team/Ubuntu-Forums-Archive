---
title: "Severe n00b: Can't get WiFI or NIC to work"
date: 2006-12-06
forum: Hardware &amp; Laptops
---

### Post by gedeyenite on 2006-12-06
Hey all:

I am a brand new, ubuntu n00b and I am getting ready to quit.

I recently installed DD on my old Dell Inspiron 1100.  I was able to combat the screen resolution problem, but now I am stuck in a catch 22:
 Every posting I come across that attempts to help me get either my WiFi (Linksys WPC54G) or on-mobo NIC BCM 3806 I believe) to work keeps directing me to DOWNLOAD things from the internet onto the ubuntu install...hmmm.

So I am at an impass.  I need to know how I can download things on a working internet Windows PC (like the one I am on right now), bring them over to the ubuntu and then install stuff to get it to work.  One example:  I can't install ndiswrapper because either 1) they direct me to svn stuff which is an INTERNET function or 2) to even get things like "make uninstall", or "make" etc, to work, I have to install the packages:  "build-essential", "checkinstall", and "libgtk1.2-dev"--all of which will then require to CONNECT TO THE INTERNET to install additional packages.

So what can I do?  Is my only hope to break down and get another wireless card that is claimed to work in ubuntu on a Inspiron 1100?  That seems to be breaking out of the realm of "free and easy" IMO.

Help desired or ubuntu is fired,

Murph](*,) :confused:

---

### Post by Malac on 2006-12-06
build-essential et al should be on the install CD just insert it and add it to Synaptic using System->Synaptic Package Manager then Settings->Repositories. It should be on the first tab "**Ubuntu 6.10**" in a section **CD/DVD**.

In a terminal:
```
dpkg-reconfigure xserver-xorg
```
Should allow you to reconfigure your resolution/monitor.

If you want to move files from Windows to Ubuntu you need a drive that both OS can see. Search for "read windows partition from ubuntu" in the forum for lots of ways to do this.

Hope this helps.

---

