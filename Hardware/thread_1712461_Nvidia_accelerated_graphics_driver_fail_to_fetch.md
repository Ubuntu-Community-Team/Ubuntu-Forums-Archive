---
title: "Nvidia accelerated graphics driver fail to fetch"
date: 2011-03-22
forum: Hardware
---

### Post by tryan3131 on 2011-03-22
I have just installed 10.10rc (meerkat) on my HP 8510w (nvidia quadro fx  570M) and cannot enable the extra visual effects or detect my secondary  monitor.  I went through *system > preferences > appearance > visual effects  *and  clicked "extra".  It searches for the drivers and tells me that I need  the Nvidia accelerated graphics driver and asks if I want to enable.  I  clicked ok and it starts to download.  When trying to "download and install" the nvidia drivers,  which it says you must do to enable "extra" visual effects, I get this  error message:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_260.19.06-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_260.19.06-0ubuntu1_i386.deb) Connection failed [IP: 91.189.88.40 80]

I have been having some trouble in the past days retrieving packages from some of the sources, but cannot figure out why.

Does anyone have any suggestions?

---

### Post by grahammechanical on 2011-03-22
There is another way to do this. Go to System>Administration>Additional Drivers and activate the Nvidia driver from there. If you are connected to the internet the driver will (should) download. Then when you go to System Preferences>Appearance>Visual Effects and click Extra then the search will be successful.

I think that the Appearance Utility only looks to see if the driver is installed so that it can activate it for its own purposes. Drivers from companies like Nvidia do not come as part of the Ubuntu installation process. That have to be installed by deliberate action on the part of the user.

Regards.

---

### Post by tryan3131 on 2011-03-22
Thanks for the suggestion, but it still is not working.

Both ways "download and install" the driver in the same manner.  When I tried doing it through additional drivers it did the same thing.  There is an option for an older version (version 173).  I will try doing that one tonight.

If I am able to get the older version to install is there an easy way to just update the driver or would that essentially download and install the latest version in place of the older (the issue seems to come from downloading the driver).

I'll post the results of the older version after I've had a chance to try it out.

---

### Post by tryan3131 on 2011-03-22
> **tryan3131 said:**
> 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_260.19.06-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_260.19.06-0ubuntu1_i386.deb) Connection failed [IP: 91.189.88.40 80]

Same error even with the older version of the driver.  This is slightly frustrating.  Is there any other place for me to get the driver even though it is proprietary?

---

### Post by Rhubarb on 2011-03-22
After a quick internet search for "nvidia-settings_260.19.06-0ubuntu1_i386.deb" I've found a mirror that should work:
[http://ftp.iinet.net.au/linux/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_260.19.06-0ubuntu1_i386.deb](http://ftp.iinet.net.au/linux/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_260.19.06-0ubuntu1_i386.deb)

---

### Post by tryan3131 on 2011-03-23
The mirror worked.  Thank you for the insight.  I should have realized that I could have looked for another mirror.

Now I'm having an issue configuring my second monitor.  Once I get the monitor options open and configure the second monitor it informs me that i can not parse the x config file.  I'll search for some solution elsewhere, but i thought i should mention it while I'm replying.

---

