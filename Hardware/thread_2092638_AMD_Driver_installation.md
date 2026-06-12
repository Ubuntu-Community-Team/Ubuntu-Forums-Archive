---
title: "AMD Driver installation"
date: 2012-12-08
forum: Hardware
---

### Post by ohellequin on 2012-12-08
Hello Ubuntu users!
I had a strange problem installing my AMD Driver. I have a "HP Pavilion g7 1110ev" Netbook and it uses a Raedon HD 6700M graphic card. Recently I reinstalled 12.10 and wanted to install the graphic driver and i used this site: [http://www.itworld.com/software/306225/install-amd-catalyst-1210-driver-ubuntu-1210](http://www.itworld.com/software/306225/install-amd-catalyst-1210-driver-ubuntu-1210). But during the installation I got an error:

 
 [IMG]https://dl-web.dropbox.com/get/Screenshot%20from%202012-12-08%2017%3A27%3A33.png?w=26227784[/IMG]

the log contains the following:

```

Supported adapter detected.
Check if system has the tools required for installation.
fglrx installation requires that the system have kernel headers.  /lib/modules/3.5.0-19-generic/build/include/linux/version.h cannot be found on this system.
One or more tools required for installation cannot be found on the system. Install the required tools before installing the fglrx driver.
Optionally, run the installer with --force option to install without the tools.
Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.

```

So, the driver didn't get installed. What should I do now to finish the installation ? Or, do I even need to install this driver ??
Thank you for your attention :)
Ori

---

### Post by 2F4U on 2012-12-08
I think that you are missing some dependencies. The first answer in this post

[http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx)

seems to have a list of what you need to install.

---

