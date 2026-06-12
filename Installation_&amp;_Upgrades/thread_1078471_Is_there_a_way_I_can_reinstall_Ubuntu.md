---
title: "Is there a way I can reinstall Ubuntu???"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by Cheater87 on 2009-02-23
The WICD program got rid of the default network finder and I can't get online and would like to reinstall Ubuntu on the partition I have it on. How would I do that???

---

### Post by konqueror7 on 2009-02-23
if only wicd is the problem, it would be a waste reinstalling the whole system...just uninstall wicd, then you can download gnome-network-manager [here]("http://packages.ubuntu.com") again from a different pc and install it...

or if you haven't cleaned your cache, try installing it in synaptics again...

---

### Post by taurus on 2009-02-23
Boot from the LiveCD.  Go to installing process and when you get to the partition part (Step 4 of 7), pick Manual option and mount the whichever partition that you use for root filesystem to / and format it.  If you have other partitions, mount them from that screen.  You don't have to do anything with the swap partition since the installer should know how to handle it.

---

### Post by imdano on 2009-02-23
If you have a ethernet cable plugged into your computer, you can just open a terminal and run
```
sudo ifconfig eth0 up
sudo dhclient eth0
```This will likely get you connected to the internet again, and you can reinstall network manager.

---

### Post by Cheater87 on 2009-02-23
I have 8.10 of Ubuntu which package do I pick???

---

### Post by Cheater87 on 2009-02-23
How would I put it on my laptop from a different computer? I have a USB drive but don't know how to install stuff from a USB drive to Linux.

---

### Post by konqueror7 on 2009-02-23
just download the *.deb packages from the [site]("http://packages.ubuntu.com") and also its dependecies, just double click it, its similar to *.exe files...

---

### Post by Cheater87 on 2009-02-24
If I put it on a flash drive how can I put it on linux?

---

### Post by imdano on 2009-02-24
Plug the flash drive into your laptop an icon for the drive will pop up on your desktop.  Open it up and double-click the .deb.

---

### Post by Cheater87 on 2009-02-25
I went to uninstall but can't find WICD. :(

---

### Post by imdano on 2009-02-25
I don't follow. ```
sudo apt-get remove wicd
```Should do the trick.  If that turns up no results then it's not installed...

---

### Post by Cheater87 on 2009-03-08
How do I get it form that site??? I click the 8.10 things and it takes me to a definition page???

---

### Post by Cheater87 on 2009-03-14
bump anyone???

---

### Post by tommcd on 2009-03-14
> **Cheater87 said:**
> How do I get it form that site??? I click the 8.10 things and it takes me to a definition page???

Scroll down the page a bit. Type network-manager in the search bar and make sure Intrepid is selected in the next section. Here are the network-manager packages:
[http://packages.ubuntu.com/search?keywords=network-manager&searchon=names&suite=intrepid&section=all](http://packages.ubuntu.com/search?keywords=network-manager&searchon=names&suite=intrepid&section=all)

---

### Post by Cheater87 on 2009-03-14
Thanks. But I Finally located it in the SPM menu. :) Got the internet back up and running.

---

