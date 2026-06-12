---
title: "Debian old-timer, confused with Ubuntu package list"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by zorzella on 2009-03-23
I've been maintaining my Debian server for well over 10 years, and consider myself proficient. So I decided to move on to Ubuntu, and, ultimately, I managed, but there were a few quirks I'd love to clear up.

What I did was a totally fresh install of Intrepit from the CD ROM (boot the CD, click install, nuke the partitions, answer questions, reboot).

Then, I started to customize (i.e. install stuff that I needed but was not there). So I went to "Applications > Add/Remove". I  searched for some application (I think it was "gimp") and installed it. So far so good.

Then I searched for "lynx", but could not find it (there were 3 "hits", including "links 2", but no "lynx"). I started to look for filters, so I made sure Show "All available applications" was chosen, and even found "System > Administration > Software Sources", where I ticked a few boxes related to "third party" stuff. Still, no "lynx".

So I fall back to the command line:

$ dpkg -l lynx*

Sure enough, it lists "lynx" and "lynx-ssl". 

Question #1: why doesn't lynx come up in the "Add/Remove" ui?

So I install lynx from the command line (note: it still did not show up in the "Add/Remove" ui), and tried it out. It did not have SSL support, so I tried to install "lynx-ssl", but that package did not exist to be installed:

zorzella@blue:~$ apt-cache policy lynx-ssl
lynx-ssl:
  Installed: (none)
  Candidate: (none)
  Version table:

Looking at forums out there, it seems this package used to exist in a previous version of Ubuntu, but (remember) this is a fresh install.

Question #2: why is lynx-ssl listed in "dpkg -l lynx*"

The forums also mentioned I should install "lynx-cur", which did not appear in the list of "dpkg -l lynx*". I tried it anyway, and, to my surprise, it worked!

Question #3: why would a package that is not even listed in "dpkg -l" be available to install?

Thanks,

Z

---

### Post by BobbyS on 2009-03-23
A good way to see what packages you have available is go to System> Administration> Synaptic Package Manager. You can search for what you want, and yes lynx is in there.

---

