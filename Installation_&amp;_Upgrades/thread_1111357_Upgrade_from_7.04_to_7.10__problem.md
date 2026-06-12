---
title: "Upgrade from 7.04 to 7.10  problem"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by shotgrape on 2009-03-30
I have been trying to upgrade from 7.04 to 7.10 but it keeps failing.  I have fully upgraded 7.04 and there was no problem there.  When I try upgrading to 7.10, it fails to fetch certain files and aborts.  A log of the messages are below.  What can I do to solve this issue?


> Do you want to start the upgrade?

12 packages are going to be removed. 136 new packages are going to be installed. 936 packages are going to be upgraded.

You have to download a total of 2254. This download will take about 0 seconds with a 1Mbit DSL connection and about 0 seconds with a 56k modem.

Fetching and installing the upgrade can take several hours and cannot be canceled at any time later.
Continue [yN]  Details [d]Y

Fetching
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main xserver-xorg-video-all 1:7.2-5ubuntu13
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main xserver-xorg-input-all 1:7.2-5ubuntu13
Done downloading
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main xserver-xorg-video-all 1:7.2-5ubuntu13
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main xserver-xorg-input-all 1:7.2-5ubuntu13
Done downloading
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main xserver-xorg-video-all 1:7.2-5ubuntu13
Failed [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main xserver-xorg-input-all 1:7.2-5ubuntu13
Done downloading

Could not download the upgrades
The upgrade aborts now. Please check your internet connection or installation media and try again.
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-video-all_7.2-5ubuntu13_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-video-all_7.2-5ubuntu13_i386.deb) Connection failed [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-input-all_7.2-5ubuntu13_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-input-all_7.2-5ubuntu13_i386.deb) Connection failed [IP: 91.189.88.31 80]

Restoring original system state

Aborting
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done


---

### Post by rjl6591 on 2009-03-30
It looks as though your internet connection wasn't working when you tried to do the upgrade. Check that it's working and try again.

---

### Post by shotgrape on 2009-03-30
I don't think it's my internet connection.   I just tried going directly to the location of these files and they appear to be missing from the site.  How can I upgrade without these packages being available from the archive?

[http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-video-all_7.2-5ubuntu13_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-video-all_7.2-5ubuntu13_i386.deb)

[http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-input-all_7.2-5ubuntu13_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-input-all_7.2-5ubuntu13_i386.deb)

---

### Post by shotgrape on 2009-03-30
That's weird, those files seem to be available from my home computer, but not at work.

---

