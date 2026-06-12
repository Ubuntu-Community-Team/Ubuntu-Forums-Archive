---
title: "What is the best way to install packages from http://packages.debian.org/"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by irate.turtle on 2009-04-19
Hi,

I want to install this package on my system

[http://packages.debian.org/squeeze/amd64/libxcb-event1/download](http://packages.debian.org/squeeze/amd64/libxcb-event1/download)

What would be the best way to do that? I read somewhere that if install .deb packages as follows:

sudo dpkg -i libxcb-event1_0.3.3-2+b1_amd64.deb

then some dependencies issues may creep in.

So how should I do it?

Is there a way to (temporarily?) include this repository for apt-get and install the packages maintaining the right dependencies>

---

### Post by irate.turtle on 2009-04-19
I used the steps given here

[https://bugs.launchpad.net/ubuntu/+source/awesome/+bug/253985/comments/10](https://bugs.launchpad.net/ubuntu/+source/awesome/+bug/253985/comments/10)

I was trying to install awesome 3.2.1

---

### Post by Mark Phelps on 2009-04-20
The easiest way to install a .deb package is to right-click on it and choose the option to open with the package manager ... however ...

When you're installing directly from .deb packages, you have to resolve the dependencies on your own.  It will tell you what's missing, but it won't go hunt it down and find it for you.

If you use the Debian package search tool, you will see a list of dependent packages on the web page for the package you want to install.

The tool is at the following link:

[http://www.debian.org/distrib/packages]("http://www.debian.org/distrib/packages")

---

