---
title: "GT 430 Ubuntu 13.10"
date: 2013-12-15
forum: Hardware
---

### Post by shaneee92 on 2013-12-15
I installed 13.10 on my system and downloaded the latest nVidia drivers  from their website. Version 331.20. I stopped the xserver I think it is  and installed the driver but upon reboot I only have an orange blinking  cursor and can't get to the GUI. I will reinstall again once I know how  to get this working as I can't get full resolution of 1600x1200x32. Managed to get some resolution but still not the required 1600x1200.

[IMG]http://i.imgur.com/ctJyWTy.png[/IMG]

This is the driver I'm using,

[IMG]http://i.imgur.com/w98RHZl.png[/IMG]

Thanks,
Shane

---

### Post by oldfred on 2013-12-16
Did you install both a download from nVidia and the nVidia driver from Software sources shown above?
If you install two different one's they conflict and cause all sorts of issues. And then you have to totally house clean all nVidia drivers and start over with just one.

Run these commands. First to see what you have, then second with version shown in first.

fred@fred-Precise:~$ [COLOR=#ff0000]dpkg -l | grep -i nvidia*[/COLOR]
ii  nvidia-319-updates                     319.49-0ubuntu0.0.1                                 NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings-319-updates            319.49-0ubuntu0.0.1                                 Tool for configuring the NVIDIA graphics driver
fred@fred-Precise:~$ [COLOR=#ff0000]sudo apt-cache policy nvidia-319-updates[/COLOR]
nvidia-319-updates:
  Installed: 319.49-0ubuntu0.0.1
  Candidate: 319.49-0ubuntu0.0.1
  Version table:
 *** 319.49-0ubuntu0.0.1 0
        500 [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) precise-proposed/restricted amd64 Packages
        100 /var/lib/dpkg/status
     319.32-0ubuntu0.0.1 0
        500 [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) precise-updates/restricted amd64 Packages

---

### Post by shaneee92 on 2013-12-16
> **oldfred said:**
> Did you install both a download from nVidia and the nVidia driver from Software sources shown above?
If you install two different one's they conflict and cause all sorts of issues. And then you have to totally house clean all nVidia drivers and start over with just one.

Run these commands. First to see what you have, then second with version shown in first.

fred@fred-Precise:~$ [COLOR=#ff0000]dpkg -l | grep -i nvidia*[/COLOR]
ii  nvidia-319-updates                     319.49-0ubuntu0.0.1                                 NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings-319-updates            319.49-0ubuntu0.0.1                                 Tool for configuring the NVIDIA graphics driver
fred@fred-Precise:~$ [COLOR=#ff0000]sudo apt-cache policy nvidia-319-updates[/COLOR]
nvidia-319-updates:
  Installed: 319.49-0ubuntu0.0.1
  Candidate: 319.49-0ubuntu0.0.1
  Version table:
 *** 319.49-0ubuntu0.0.1 0
        500 [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) precise-proposed/restricted amd64 Packages
        100 /var/lib/dpkg/status
     319.32-0ubuntu0.0.1 0
        500 [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) precise-updates/restricted amd64 Packages

I didn't install anything for it they were already the options for the drivers.

---

### Post by oldfred on 2013-12-16
What do command shows as to installed versions.

Have you run nVidia X-server settings?

---

