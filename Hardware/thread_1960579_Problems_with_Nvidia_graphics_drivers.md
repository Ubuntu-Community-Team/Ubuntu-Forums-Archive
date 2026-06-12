---
title: "Problems with Nvidia graphics drivers"
date: 2012-04-17
forum: Hardware
---

### Post by arcelivez on 2012-04-17
Hello,

well I bought a new laptop yesterday, an Acer Aspire 5750G and tried to install Ubuntu 12.04 Beta2 Ubuntu on it.[https://friendly.ubuntu.com/11.10/Acer/Aspire%205750G/I:CL9W0p:E4:I8g:Ui:BEfp:vc:BHe:Uj:BEfp:E4E:BYQ:Ovw:BF7/]("https://friendly.ubuntu.com/11.10/Acer/Aspire%205750G/I:CL9W0p:E4:I8g:Ui:BEfp:vc:BHe:Uj:BEfp:E4E:BYQ:Ovw:BF7/")

As the site above states I can see that the video card drivers should work fine, however Ubuntu won't recognize my video card. The default video drivers seem to work fine, but it says there are no proprietary additional drivers available. It also under System description says that the Video driver is unknown. I tried installing the drivers from the Nvidia site, but after installing them it just got worse: it loaded the desktop with 640x480 and there were no other resolutions available anymore. I assume the Nvidia driver wasn't loaded correctly, because I couldn't find Nvidia xserver settings. I even tried running some command, maybe nvidia-settings or nvidia-xsettings (can't remember exactly), but  it said nvidia driver wasn't ON or something like that.

I'm also trying to backup old xorg.conf file, but it says "read-only file system" and doesn't allow me to do anything or modify the file anymore when I try to go in recovery mode and access it from root shell prompt.

So does anybody know why my video card doesn't get recognized properly and why do I seem to have so many problems after installing the driver from Nvidia site? Should I use Ubuntu 11.10 instead of 12.04? Would that help?

---

### Post by mbudd on 2012-04-17
The problem might be the Optimus technology used with your graphics chip. Check out the Bumblebee project [http://bumblebee-project.org/](http://bumblebee-project.org/) to see if it helps.
Marvin

---

