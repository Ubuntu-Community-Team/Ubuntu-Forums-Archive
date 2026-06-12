---
title: "Driver Manager thingy..."
date: 2008-08-20
forum: General Help
---

### Post by infinitelink on 2008-08-20
So I used the LiveCD for Kubuntu and made modifications, then installed. When I installed the modifications didn't take effect as they usually do.

So I restarted on the newly installed system. One of the weird things, though, is that on the install the Hardware Drivers Manager is screwy.

It seemed to do the ATI thing fine, but on clicking the checkbox for the Broadcom the "In Use" status goes to "Needs Computer Restart" without ever bringing-up the Adept manager to download the needed firmware, extract, and install it. 

It did that fine on the LiveCD, but won't now. : (  And then even if I start it up in Konsole (using Kubuntu) with sudo it gives the same. After doing the supposedly needed restart the same behavior just recurs. 

All my sources.list locations are enabled too, by the way. Any help? Perhaps re-installing the Hardware Drivers Manager, or...?

---

### Post by infinitelink on 2008-08-20
Okay, so very very luckily, I may have found a solution; however since this tool is supposed to make things easy for complete newbs, this needs fixing right away. (Also with the detail that it doesn't always get permissions and demands that a command be run without giving specifics, and the fact that the Kubuntu install hasn't turned-over the permissions from the LiveCD install to the user!). Anyone know how to file a bug report?

Besides this, here's the possible solution
[http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/](http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/)

I'm about to try a restart...cross your fingers!

---

### Post by infinitelink on 2008-08-20
Okay, so that doesn't fix the bunk Hardware Drivers Manager (of course), but it is a solution to getting the firmware up and running (restart worked after all that).

---

### Post by adam_kimber on 2008-08-20
Ubuntu has a lauchpad bug tracking system .. [https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

---

