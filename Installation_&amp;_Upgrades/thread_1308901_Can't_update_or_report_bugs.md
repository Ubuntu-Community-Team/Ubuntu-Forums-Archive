---
title: "Can't update or report bugs"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by tacantara on 2009-11-01
After an upgrade turned my machine into a mess, I did a fresh reinstall of 9.04 and ran the upgrade to 9.10 again.  The upgrade process went relatively smoothly, and I had wireless upon reboot (one of the problems I had the first time was missing wifi capability).  However, now there's a new set of problems:


[LIST]
[*]The error reporting feature is broken
[*]I can't apt-get or download packages from Synaptic. This is a big problem, as this update removed things like ubuntu-restricted-extras.  So much for going to websites that utilize Flash, or playing audio files.  This error also extends to the "Ubuntu Software Center."  And, yes, my internet connection is working just fine.
[/LIST]
These are the problems I've discovered so far.  I'd file a bug report, but with the amount of info they need to troubleshoot, I don't have enough for them to work with.  If I can't figure it out, I may just revert to 9.04....or try out this Fedora 11 disk that came in a Linux magazine.  Options :)

---

### Post by cariboo on 2009-11-01
Bug reporting has changed, To report a bug press Alt-F2 and type:

```
ubuntu-bug <packagename>
```

As far as not being able to download updates, check your dns by opening a terminal and typing:

```
ping 74.125.95.105
```

If that works, then type:

```
ping www.google.com
```

If the second command doesn't work, edit your connection in Network-Manager to set dns manually.

---

### Post by tacantara on 2009-11-02
I reinstalled 9.04, downloaded all updates, then downloaded the 9.10 upgrade.  Upon reboot, the wireless was still working.  I checked Synaptic and the Software Center, and both worked when I downloaded packages this time.

---

### Post by acreech on 2009-11-03
I just updated from 9.04 to 9.10 with the update manager. I am on a 64 bit system. Everything seems to be working well, except the synaptic package manager crashes when I attempt to install a program. The Software Center works fine. 

I tried the ping and they both seemed to work fine. I have not found a solution yet to the synaptic package manager crashing.

---

