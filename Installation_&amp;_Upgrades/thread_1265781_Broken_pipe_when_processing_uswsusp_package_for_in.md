---
title: "Broken pipe when processing uswsusp package for install"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by christopherbalz on 2009-09-13
When attempting to upgrade from 8.10 to 9.04 (machine is IBM ThinkPad R51 with ATI Mobility Rage Pro graphics card), a utility reported a problem with package 'uswsusp'.  

So I uninstalled that package using apt-get ('remove') and then did:

apt-get install uswsusp

That results in:

Unpacking uswsusp (from .../uswusp_0.8-1.1ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/uswsusp_0.8.1-1ubuntu3_i386.deb (--unpack):
trying to overwrite `/usr/sbin/s2disk', which is the diverted version of '/sbin/s2disk'
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
/var/cache/apt/archives/uswsusp_0.8-1.1ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried deleting that file (the .deb file) and re-installing but no change.

Since previously certain video drivers would interfere with 's2disk', and since I am getting this package error with 's2disk', I suspect that it may be the root of the problem with the completely garbled screen I've had since attempting the upgrade ( companion query: [http://ubuntuforums.org/showthread.php?p=7936075](http://ubuntuforums.org/showthread.php?p=7936075) ).

All ideas welcome.  Thank you in advance.

---

### Post by christopherbalz on 2009-09-14
Solution that worked for me was to:

a) Completely uninstall 'uswsusp' (used Synaptic for that - "Mark for complete removal")
b) Reinstall hibernate and all default 'pmi' utilities (not sure this is necessary)
c) Return to the Ubuntu defaults from which I had departed due to previous video driver use that conflicted with the defaults, with the commands below from this wiki: 

[http://forums.msiwind.net/default-msiwind/ubuntu-can-suspend-more-than-once-t854.html](http://forums.msiwind.net/default-msiwind/ubuntu-can-suspend-more-than-once-t854.html)

sudo dpkg-divert --rename --remove /usr/sbin/pmi
sudo dpkg-divert --rename --remove /usr/sbin/pm-suspend
sudo dpkg-divert --rename --remove /usr/sbin/pm-hibernate

---

