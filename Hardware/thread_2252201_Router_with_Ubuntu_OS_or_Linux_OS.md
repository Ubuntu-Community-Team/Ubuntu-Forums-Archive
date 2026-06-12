---
title: "Router with Ubuntu OS or Linux OS"
date: 2014-11-10
forum: Hardware
---

### Post by erotavlas on 2014-11-10
Hi,

I would like to buy a new router with the following features: gigabit ethernet, wireless N, USB port for HDD and Linux OS, possibly Ubuntu. Can you tell me if there exists something like this?
I know about of openWRT project but I do not appear very updated for many routers. I would like to have a device which is able to run project like ownCloud, mailPile, bitTorrent sync and etc.

Thank you

---

### Post by weatherman2 on 2014-11-10
You might look into DD-WRT or TomatoUSB Linux-based firmwares.  TomatoUSB runs only on Broadcom-based routers.  DD-WRT will run on others but not always very well.  I don't think putting Ubuntu on one of these is likely, but you can get the source code for DD-WRT or TomatoUSB to make changes if you wish.

I can recommend the Linksys/Cisco E3000 router that meets all of your criteria.  Works great for me with TomatoUSB.

---

### Post by sandyd on 2014-11-10
> **erotavlas said:**
> Hi,

I would like to buy a new router with the following features: gigabit ethernet, wireless N, USB port for HDD and Linux OS, possibly Ubuntu. Can you tell me if there exists something like this?
I know about of openWRT project but I do not appear very updated for many routers. I would like to have a device which is able to run project like ownCloud, mailPile, bitTorrent sync and etc.

Thank you

Many routers do not have that capability because they are outside of what a normal router usually does (which is function as an internet/nat gateway). If you want though, a nice idea would be to use a small server on the LAN such as a raspberry pi.

---

### Post by erotavlas on 2014-11-10
Thank you for your answer. I take a look at DD-WRT and TomatoUSB projects. Unfortunately, I have no budget to buy your router Linksys/Cisco E3000. I'm thinking about netgear WNDR3700 v4 which is compatible with all projects DD-WRT, TomatoUSB and openWRT and it costs two-three time less that your. What do you think of it?
Moreover, are you able to install custom software by using these firmwares? For example can you install this [http://owncloud.org/install/](http://owncloud.org/install/) in your router?

Thank you

---

### Post by erotavlas on 2014-11-10
> **sandyd said:**
> Many routers do not have that capability because they are outside of what a normal router usually does (which is function as an internet/nat gateway). If you want though, a nice idea would be to use a small server on the LAN such as a raspberry pi.

Yes, I thought at this solutions. Is there a way to use the USB port of a router plus and HDD as remote synchronized storage (that is a cloud like storage)? In the scenario of many peoples which share files and do not want to use cloud services, but they want to host their own cloud, how can I do? Can I avoid to buy a raspberry pi or something similar?

Thank you

---

### Post by ian-weisser on 2014-11-10
I generally recommend against installing extra services on your router.
When the service crashes your router and takes down your network connection...it's hard to use a non-working connection to look up how to identify and fix the problem.
If you don't have another way to access the internet available to you, leave the router alone.

Also, all hardware fails eventually. If your new, customized router  fails in two years, are you willing to do all that customization again  on a different new router?

My first server was an obsolete laptop. Great for learning - small, quiet, self contained, portable, and familiar. The family appreciated a server that could be closed and put away at dinnertime...and still quietly run.

---

