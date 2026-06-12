---
title: "gateway 200"
date: 2005-04-27
forum: Hardware &amp; Laptops
---

### Post by ryness on 2005-04-27
i've installed ubuntu on a Gateway 200 laptop and am wondering if there's anyone else out there familiar with this model? i'm just curious as i'm trying to get some things working like suspend, the scroll wheel, and getting the battery meter to show accurate.

---

### Post by Sgood1971 on 2005-05-06
[QUOTE=ryness]i've installed ubuntu on a Gateway 200 laptop and am wondering if there's anyone else out there familiar with this model? i'm just curious as i'm trying to get some things working like suspend, the scroll wheel, and getting the battery meter to show accurate.[/QUOTE]

I have Ubuntu on a Gateway 200STM, it does not have a scroll wheel but suspend and the battery meter work fine. I had to add acpi=off to menu.lst and add apm to modules. And also add shpchp and pciehp to /etc/hotplug/blacklist.

See [this](http://www.ubuntulinux.org/wiki/SuspendHowto) link.

HTH

---

### Post by ryness on 2005-05-07
thanks, your tips and that link helped - i can now hibernate and suspend the laptop.

the battery meter, tho, still shows inaccurate numbers. anyone have any tips on getting that to work?

---

### Post by Sgood1971 on 2005-05-07
Mine was inaccurate too, I straightened that out by going into the BIOS and running 'Smart Battery Calebration'. Only do this when you have a lot of time as it takes a while, I would reccomend before going to bed. Also, check your owners manual or go to Gateway support, enter your serial # so you get the right product and download an owners guide if you don't have one. I can't remember if you need to start the process with the battery charged or discharged. Post back here on the results in case someone else is searching for this.

Good Luck O:)

---

### Post by briguy on 2005-09-09
I have a Gateway 200x and was initially using the initrd / DSDT message for fixing the battery monitoring.  However, I just installed Breezy and the battery monitoring there worked out of the box.

However, I can't get hibernate to work!  Can you post your /etc/default/acpi-support file?

Thanks

---

### Post by fadumpt on 2006-07-17
with the Gateway 200STM, have any of you figured out how to make hot-docking working?  As far as I know, the Dock works fine if I boot up with it docked, but when I undock and re-dock, I lose optical drive functionality (usb still worked, haven't tried anything else)  There is that button on the front for hot-undocking, is there a way to implement that in Linux?  

Thanks.

---

### Post by briealeida on 2007-07-13
I have a GW 200 and I've had Knoppix, Slackware, Fedora and Ubuntu on it. Few issues glad to know I'm not the only one anymore. 

I've had the same issue with docking and undocking. There was one OS with which I didn't experience that problem.

Sucks that I can't remember anymore.

---

