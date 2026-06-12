---
title: "No graphics card detected for a specific user"
date: 2011-11-04
forum: Hardware
---

### Post by laserrain on 2011-11-04
So about a week ago, I noticed one user on my laptop has no nice desktop effects anymore, yet everything's fine for the others. 

Some details: Ubuntu 11.04, ATI Radeon Mobility X1600 (yep, it's an old laptop)
When I try to re-enable effects from system/administration/appearance as the user without effects, I get a message saying no graphics driver is installed. However, given everything's fine for other users, this isn't the case and the driver is working.

But I can't work out what driver that is, lspci -v doesn't list one, can't see one in xorg.conf (but I'm not too experienced so that's the extent of my search). I haven't installed the proprietary ATI driver, although I did try (after the problem), but I haven't been using it up to now anyway.

I know it isn't the end of the world and I can just replace users with new ones, I just want to know what on earth happened! 

This is my first post so I hope it's in the right place, any help very much appreciated!

---

### Post by pme 72 on 2011-11-06
Interesting problem. I do not have any answers but do recommend avoiding installing the proprietary fglrx driver with your x1600 card as it is no long supported by the Catalyst driver. There are instructions here for uninstalling the fglrx driver should you decide to attempt to go that route. 

[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)

It almost sounds like the user without DE effects is limited to the Vesa driver. I did not know that it was possible for different users on one installation to have different drivers.  

```
sudo lshw -c display
```

That code should reveal video chip and driver but 

```
lspci -v
```

should have worked too.

---

### Post by laserrain on 2011-11-06
Thanks for the reply, you're right about fglrx issues, after reading the guide you suggested everything is back to normal and working perfectly so thanks a lot! 

For the sake of completeness for anyone else with this issue, I did this (quoted from Lucid Installation Guide): 

```
$ sudo sh /usr/share/ati/fglrx-uninstall.sh
$ sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
```
If you plan on using open-source drivers, you will need to reinstall some packages because Catalyst overwrites or diverts some key 3D libraries with proprietary versions. For more information on this issue, see this Ubuntu wiki page
```
$ sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
$ sudo apt-get install xserver-xorg-video-ati
$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Marking as solved :D

---

