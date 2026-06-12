---
title: "Intel Graphics HD 4000 video controller?"
date: 2013-06-23
forum: Hardware
---

### Post by alvinmoneypit on 2013-06-23
Building a new computer and trying to stay on top of potential problems.

I wish to use Intel's on board video HD4000 for this computer.  Couldn't find much on it, not even at [Intel,]("http://www.intel.com/content/www/us/en/homepage.html") but I did find [this page]("https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.1") from 01.org that offers downloads for Ubuntu that portends some control of the video on Intel's on board video system.

Do I need this download installed properly to get the full function of my video or will the Ubuntu supplied controllers work fine for the chip embedded video?

I don't do that much adjusting my system so I'm not sure if I can competently follow that HowTo on the previously mentioned 01.org page - is there a more comprehensive, dumbed down version somewhere?

---

### Post by jp734 on 2013-06-24
Well, for the most part, distros own drivers work. If they don't have the driver for your card, VESA driver always works. Then you can just download the driver you found if you want to.

---

### Post by Mark Phelps on 2013-06-24
Intel video drivers are installed automatically as part of the initial setup.  You don't need to install drivers on your own -- this is not Windows.

---

### Post by Yellow Pasque on 2013-06-24
> **alvinmoneypit said:**
> I did find [this page]("https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.1") from 01.org that offers downloads for Ubuntu .. Do I need this download installed properly to get the full function of my video or will the Ubuntu supplied controllers work fine for the chip embedded video?

No, this ain't Windows...
Default/stock drivers hsould work fine, and if you really need the latest intel drivers, xorg-edgers offers a PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=raring](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=raring)

---

### Post by alvinmoneypit on 2013-06-24
Thanks for these replies.

I ask because the author of [this thread]("http://ubuntuforums.org/showthread.php?t=2120071") here can't control his video temperature on the exact video controller I plan on installing, so I thought I better ask.

---

