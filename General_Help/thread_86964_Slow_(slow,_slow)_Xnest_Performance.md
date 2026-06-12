---
title: "Slow (slow, slow) Xnest Performance"
date: 2005-11-06
forum: General Help
---

### Post by ttague on 2005-11-06
Hi All:

I've set up Breezy on a rather elderly laptop to use as a central storage server. When I am working with the system - in GNOME or KDE - locally, the speed of performance is about what I'd expect.

When I use Xnest to access the machine remotely the performance slows to an absolute crawl. 2-10 seconds to drop a menu, etc, etc. 

I have other Linux boxes (others distro's) on the same network, hanging off the same hub, where this is not a problem. For these systems speed over the network is very close to speed when use with the attached display.

These speed issues start right at the login panel - immaterial what I'm logging in to. Also - the speed issues don't feel like just network bandwidth/latency - the machine is really struggling to open applications - but this is just a subjective observation.

I'd appreciate some pointers on where to start looking.

TT

---

### Post by bernardfrancois on 2006-03-03
I have the same problem. I want to acces the desktop of a faster computer (sempron 2600+, ubuntu beezy) trough a slower computer (pentium II 366mhz, ubuntu hoary).

Maybe playing with the parameters passed to Xnest might speed it up a bit? Or maybe my slow computer is too slow to bring all those pixels to it's screen...

---

### Post by ttague on 2006-03-03
At least in my case this doesn't seem to be a machine speed related issue. I have a variety of machines around from OS X to beefy to wimpy and aged. All of these machines can Xnest into any of the others and get good to excellent performance - unless you're trying to attach to a Ubuntu machine.

Initially I thought this was a problem going from OS X's version of X to Ubuntu - but I've now verified that it occurs in CentOS and Fedora. The initiall presentation of the login screen and window opening is so slow as to make the remote X session unusable with Ubuntu.

Any ideas would be appreciated.

---

