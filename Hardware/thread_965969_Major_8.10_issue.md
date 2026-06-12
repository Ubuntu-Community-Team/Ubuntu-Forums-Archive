---
title: "Major 8.10 issue"
date: 2008-11-01
forum: Hardware
---

### Post by TheHybrid520 on 2008-11-01
I'm enjoying 8.10 for the most part but I can't install software without having this pop up "Media change: please insert the disc labeled
 'Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)'"

I have no idea why this keeps popping up, it is causing major issues, I can't anything.

---

### Post by phidia on 2008-11-01
The package manager wants you to insert the install disk-the disk you used to install ubuntu with.

---

### Post by TheHybrid520 on 2008-11-01
I only downloaded the update ISO file. can I use that? Also why does it need the disk now and not back in 8.04?

---

### Post by fornix on 2008-11-01
Because the CDRom is in your repository. If you remove that, your problem will be solved...
To remove this, do the following.
Open the file $ sudo gedit /etc/apt/sources.list
or $ sudo kate /etc/apt/sources.list

Find a line something similar to this
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted

Comment this line by putting a # in front of it.
Comment all similar lines starting with deb cdrom:
Then run a $ sudo apt-get update

---

### Post by phidia on 2008-11-01
I guess that is a solution although packages like build-essential are on the cd and relieve the servers from everyone trying to grab everything from there.

---

### Post by TheHybrid520 on 2008-11-01
> **fornix said:**
> Because the CDRom is in your repository. If you remove that, your problem will be solved...
To remove this, do the following.
Open the file $ sudo gedit /etc/apt/sources.list
or $ sudo kate /etc/apt/sources.list

Find a line something similar to this
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted

Comment this line by putting a # in front of it.
Comment all similar lines starting with deb cdrom:
Then run a $ sudo apt-get update

I owe you, well both of you, my thanks. So far it seems like that worked. Thanks. :KS

---

