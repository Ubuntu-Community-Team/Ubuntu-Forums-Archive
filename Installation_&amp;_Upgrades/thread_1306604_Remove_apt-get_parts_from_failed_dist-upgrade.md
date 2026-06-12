---
title: "Remove apt-get parts from failed dist-upgrade"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by mogie on 2009-10-30
Hello everybody!

I've got some problems after having tried to dist-upgrade my 8.04.3 LTS server to 8.10 recently. 

Now I can't get to install anything because apt-get says I have to install the remaining packages from the dist-upgrade.

The problem is that the *linux-image-server 2.6.24-35.deb* package is damaged and not authenticated by dpkg. 

I'm not even able to remove the "half" installed distro, and do not know how to fix this, cause I've tried:

apt-get autoclean
apt-get -r install (which I get a message about every time I try to install anything now, but of course fails because of the "damaged" package or something)
apt-get autoremove.. 


Is there anything other I could try to "clean" this? Or do I need to find the package which is screaming about getting these dependencies installed? It is not mentioned in the warning I get because I've tried all the packages.

Thanks for helping!

---

### Post by XDevHald on 2009-10-30
Boot into (recovery mode) using the kernel you're on now and do "Fix and repair broken packages." This WILL fix the issue you're running into and then update-manager -d into your terminal when you boot up again.

---

### Post by mogie on 2009-10-30
It won't.

I have not update-manager installed from before of, and here is some output that may help: (I've tried to translate it from norwegian)

> You may want to execute "apt-get -f install" to fix these packages:
Following packages have not met independencie relations:
	linux-image-server: dependent by linux-image-2.6.24-25-server but is not to be installed
	linux-ubuntu-modules-2.6.24-25-server:dependent of linux-image-2.6.24-25but is not to be installed


update-manager:  Dependent of: gconf2 (>= 2.10.1-2) but is not to be installed
                  Dependent of: gksu but is not to be installed
                   Dependent of: python-dbus but is not to be installed
                   Dependent of: python-gconf but is not to be installed
                   Dependent of: python-glade2 but is not to be installed
                   Dependent of: python-vte but is not to be installed
                   Dependent of:synaptic (>= 0.57.8) but is not to be installed
E: Not met dependencies. Try «apt-get -f install» without packages 

---

### Post by XDevHald on 2009-10-30
Ok do this. The packages that are listed inside the quote you provided can be installed by doing this:

1) Open Synaptic (not your terminal) this way we can see exactly what the name of the files are to install as the output could provide differently.

2) Once Synaptic is open, type in the exact name that is provided and right click on it and choose **Mark for complete install**. Do this with every package that is listed in the above quote.

Do not do a force install without these dependencies/packages as they are needed to complete your install and to make your platform work properly.

---

### Post by mogie on 2009-10-30
I have no X-graphical mode. Only terminal.

Is there any other way? :)

---

### Post by XDevHald on 2009-10-30
Download the following from Synaptic: linux-image-2.6.24-25-server - linux-ubuntu-modules-2.6.24-25-server and linux-image-2.6.24-25

See if you can search for these in Synaptic and download them if Synaptic allows it. Keep us posted.

---

### Post by mogie on 2009-10-30
> **XDevHald said:**
> Download the following from Synaptic: linux-image-2.6.24-25-server - linux-ubuntu-modules-2.6.24-25-server and linux-image-2.6.24-25

See if you can search for these in Synaptic and download them if Synaptic allows it. Keep us posted.

I don't have Synaptics installed. How do I use it in terminal anyway?

---

### Post by mogie on 2009-10-30
Correcting dependencies : Segmentation fault

it says when I try to apt-get install -f in recovery mode (root).
I'm not able to install any package in any way by using apt-get right know. Dont know how to get these Synaptics either.

---

### Post by mogie on 2009-10-30
> **mogie said:**
> Correcting dependencies : Segmentation fault

it says when I try to apt-get install -f in recovery mode (root).
I'm not able to install any package in any way by using apt-get right know. Dont know how to get these Synaptics either.

Wahahah :D
Ran rm -rf /var/cache/apt/*.bin
and apt-get install -f again.

Fixed !

Source: [http://www.linuxforums.org/forum/debian-linux-help/80216-apt-get-segmentation-fault.html](http://www.linuxforums.org/forum/debian-linux-help/80216-apt-get-segmentation-fault.html)

**Error is back again**

Tried an do-release-upgrade and now tings are back with the same errors.

---

### Post by mogie on 2009-10-30
Found a temporarily solution: 

[https://lists.ubuntu.com/archives/ubuntu-users/2007-January/104520.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-January/104520.html)

---

