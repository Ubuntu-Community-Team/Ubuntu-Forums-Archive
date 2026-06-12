---
title: "Gateway CX210X Tablet drivers"
date: 2010-05-09
forum: Hardware
---

### Post by Ronin51 on 2010-05-09
I'm new to ubuntu. Long story short; I attempted to upgrade my GW CX210 from XP to Vista. The installation failed, but Vista made changes that prevented XP from being reloaded. After two days of screwing around with attempting to slipstream IDE drivers to an XP install disk and trying to flash the bios to accept Vista I gave up. I nuked the HD and installed ubuntu. I was up and running in 30 minutes. I'm a believer.

Only problem is the tablet doesn't work. This is a Finepoint not a Wacom screen. I did a search of this site and found a number of discussions and links. However, all were a couple of years old and seemed quite complicated for someone with modest computer skills and even more daunting for someone new to this system.

I'd just like to find out if anyone knows of any current solutions to getting a Finepoint tablet working with ubuntu. If not I'll follow one of the older recommendations. 

As I said, I'm new to this system and open source. I am truly amazed. 

GB

---

### Post by Favux on 2010-05-09
Hi Ronin51,

Welcome to Ubuntu forums!

They just built the  fpit driver for Lucid.  See:  [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=lucid](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=lucid)  Click on the _[COLOR="Blue"]View package details[/COLOR]_ to the right of the Lucid filter and that will give you the version to download.  Then click on the fpit driver and it'll give you a choice of downloads.  Chose the deb for your install 32 or 64 bit.  Once the deb is downloaded on your desktop double click on it and it will install the driver.

Hope this helps.

---

### Post by Ronin51 on 2010-05-11
Hi Favux,
I missed your initial reply - the trouble with using more than one computer.

My first attempt hasn't worked. I believe I got this right. I followed your link to launchpad.net. I did View the package. However, initially I couldn't find 'fpit'. I filtered for fpit and it identified only one item. When I expanded that I had choices for AMD64 and i386 builds. I know I'm not running 64 so, I picked i386 and downloaded = xserver-xorg-input-fpit_1.3.0....................deb.

I saved it and installed it using the DEB installer. I got a message "older version is available on a software channel and may be better supported." I closed it and continued the installation. The installation seemed to go normally - lots of progress bars and when it finished the boxes closed.

I rebooted and the tablet still doesn't work. I know I went into a lot of detail, but if I did something wrong I'd like to know. In any case I'm going to try again later today.

I do appreciate the help. I am really impressed with ubuntu, but it is a bit intimidating for a newbie.

---

### Post by Favux on 2010-05-11
Hi Ronin51,

It could be the package didn't include configuration files.  It really should but sometimes they don't and you have to make your own.  So check in /usr/lib/X11/xorg.conf.d/ and see if there is a .conf file called something like fujitsu.conf or fpit.conf.  If there is post the contents.

---

### Post by bornagainlinux on 2010-05-11
Hi Favux,

I am having the same problems. I downloaded and installed the file:
xserver-xorg-input-fpit_1.3.0+git20100504.a7e1d84c-0ubuntu0sarvatt_i386.deb

I also for a message warning that another version was available etc and continued anyway. Rebooted and nothing. I just now checked for the files you suggested

>  So check in /usr/lib/X11/xorg.conf.d/ and see if there is a .conf file  called something like fujitsu.conf or fpit.conf.

and these files do not exist. I have also seen in other posts about a file xorg.conf and I cannot find that file either.

Thanks again. 

Don

---

