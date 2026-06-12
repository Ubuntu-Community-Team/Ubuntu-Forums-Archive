---
title: "Broken packages in Ibis. Unable to fix."
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by bobdobbs on 2009-02-19
Hi all.

I wanted to install k3b on ibis. so...
apt-get install k3b

However, this uninstalled a whole lotta stuff, including quanta, which I need.

I tried to reinstall quanta with apt-get.
This failed with an error about broken packages.


At the moment, any attempt to do anything results in an error message concerning broken packages.

apt-get -g install returns:
```

 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper-kde3
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How can I fix my package managment, and install both quanta and k3b side-by-side on ibis?

---

### Post by taurus on 2009-02-19
Did you add any "extra" repos to your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by bobdobbs on 2009-02-19
> **taurus said:**
> Did you add any "extra" repos to your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

Apart from the default, I have the following extra repos referenced:

```

#moblock

deb http://moblock-deb.sourceforge.net/debian intrepid main
deb-src http://moblock-deb.sourceforge.net/debian intrepid main

#for xmms
deb http://www.pvv.ntnu.no/~knuta/xmms/intrepid ./
deb-src http://www.pvv.ntnu.no/~knuta/xmms/intrepid ./

# pulseaudio fixes
# http://ubuntuforums.org/showthread.php?t=789578
deb http://ppa.launchpad.net/psyke83/ubuntu intrepid main
deb-src http://ppa.launchpad.net/psyke83/ubuntu intrepid main


# amarok 2
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main

```

---

### Post by taurus on 2009-02-19
Maybe the last repo causes a havoc on your machine.  What if you edit /etc/apt/sources.list and comment it out and see if that fixes it.

```
**[COLOR="Blue"]#[/COLOR]**deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main
```
Don't forget to run **sudo apt-get update** first after you've edited /etc/apt/sources.list.

---

### Post by bobdobbs on 2009-02-19
> **taurus said:**
> Maybe the last repo causes a havoc on your machine.  What if you edit /etc/apt/sources.list and comment it out and see if that fixes it.

```
**[COLOR="Blue"]#[/COLOR]**deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main
```
Don't forget to run **sudo apt-get update** first after you've edited /etc/apt/sources.list.

Alas, removing the repo(and then updating) did not help.
The error persists.

I'm beginning to worry now.
A broken package management system can render my system pretty much useless.
I don't want to do a massive backup and reinstall process. But I've had apt break a few times on me, and every time I've had to reinstall.

---

### Post by taurus on 2009-02-19
Well, if you add a third party repo because you just want something new, then it would install all the new dependencies for you so eventually, something will break.  My systems never break once since Ubuntu first came out because I've never added those "repos" to my /etc/apt/sources.list.  Since you added a repo for KDE4 while some KDE's apps are still running KDE3, kio-umountwrapper-**kde3**, that could be your problem there.

---

### Post by bobdobbs on 2009-02-19
> **taurus said:**
> Well, if you add a third party repo because you just want something new, then it would install all the new dependencies for you so eventually, something will break.  My systems never break once since Ubuntu first came out because I've never added those "repos" to my /etc/apt/sources.list.  Since you added a repo for KDE4 while some KDE's apps are still running KDE3, kio-umountwrapper-**kde3**, that could be your problem there.

I see.

Any idea how I can fix it?

---

### Post by bobdobbs on 2009-02-20
Possible fix found.

I followed the instructions on this page, applying them to kio-umountwrapper-kde3.

[http://www.cyberciti.biz/tips/troubleshooting-debian-ubuntu-package-upgrades-removals.html](http://www.cyberciti.biz/tips/troubleshooting-debian-ubuntu-package-upgrades-removals.html)

I was able to then install quanta and k3b.

So far, all is working.
MY fingers remain crossed.

---

