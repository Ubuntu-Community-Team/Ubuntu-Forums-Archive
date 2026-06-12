---
title: "[SOLVED] Manually Installing Packages with Cyclic Dependencies"
date: 2008-07-31
forum: General Help
---

### Post by sephirothrr on 2008-07-31
I accidentally posted this as a reply to another thread, but I meant to put it here.
I have a laptop, and I need build-essential to install the madwifi drivers. Since I have no way of accessing the internet (no ethernet, etc) without wifi, I have taken the task of installing all the dependencies by hand. However, there are two packages that depend on each other. How do I install them?
The two packages in question are libstdc++6-4.2-dev and g++-4.2

---

### Post by ibuclaw on 2008-07-31
Are you sure that you can't connect hard-wired to the internet?
If you have an ethernet cable, connect your laptop up, then open a terminal and type in.
```
sudo ifconfig eth0 up
```
And you'll get an internet connection via ethernet.

Also, check your restricted drivers and make sure that they are enabled.
**System->Administration->Hardware Drivers**

Hardware devices that require Madwifi Drivers are enabled in there.

Also, what card do you have?
```
lspci | grep Network
```

Regards
Iain

---

### Post by sephirothrr on 2008-07-31
I can't connect because I have nowhere to connect to...
My source of internet is a nearby free AP.
I'm using Windows Vista in order to be on here, and manually downloading packages, transferring to the Ubuntu partition, and rebooting to install.

My card is an Atheros AR5700G.

---

### Post by ibuclaw on 2008-07-31
Ah, Ath5ks... my arch enemy :) (It interferes with my ath_pci card)
These are new modules with the next Ubuntu release, so hopefully you won't run into any wireless trouble when intrepid is released.

But, in the meantime.

```

build-essential
dpkg-dev
g++
gcc
libc6-dev
make
linux-headers-(your kernel version number)
#type in "uname -r" to find out what it is...

```
I think that is all that is needed.

Regards
Iain

---

### Post by unutbu on 2008-07-31
If you ever run into debs that depend on one another, you can install them by putting them in a directory by themselves and running

```
dpkg -i *.debs
```

Somehow dpkg is able to resolve dependency issues when all the debs are listed/globbed in one command.

---

### Post by sephirothrr on 2008-08-01
Thanks. Worked like a charm.

---

