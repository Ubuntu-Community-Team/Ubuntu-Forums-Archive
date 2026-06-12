---
title: "Epson Perfection V30 Scanner"
date: 2009-10-08
forum: Hardware
---

### Post by ekpyyrotic on 2009-10-08
Hello all! Longtime linux user, first time Ubuntu user here. Cool distro so far, but I've hit a little snag.

Before I begin, yes I've searched the forums and Google already, and no, my problem hasn't already been described, at least not as far as I can tell.

I'm trying to get an Epson Perfection V30 USB scanner to work on Kubuntu 9.10 beta. Installed libsane, xsane, iscan, and proprietary sane backend from Avasys. Edited /etc/sane.d/dll.conf, etc., etc. Scanner works fine as root, but no dice for ordinary users.

Here's the output of scanimage -L as both user and root:

```

scanimage -L
device `epkowa:interpreter:002:003' is a Epson (unknown model) flatbed scanner
``````

$ sudo scanimage -L
device `epkowa:interpreter:002:003' is a Epson Perfection V30 flatbed scanner
```I checked, and the 'scanner' group didn't exist, so I created it, added users to it, still no luck. Strangely, my /etc/udev/rules.d/ doesn't contain any rules for the scanner. Should I write some? How would I do that? I'm a total udev noob.

Another suggestion I found on Google was to set permissions in /proc/bus/usb/, but that folder is empty for me.

Thanks in advance for any help you guys have.

---

### Post by ekpyyrotic on 2009-10-08
Two new things:

1.
```

sudo chgrp scanner /dev/bus/usb/001/008
``` Fixes it temporarily, but I still need a udev rule to make it so I don't have to run the command every time I reboot. 

2. I seem to have contracted the [ever-increasing device number]("https://launchpad.net/ubuntu/+source/sane-backends/+bug/25970") problem.

---

### Post by boba1120 on 2009-11-18
Hi!  I was just wondering on another thread if anyone's had any success with Avasys, specifically with the V30.  Regarding your specific issue, I don't know much about udev either, but I did notice that when you download from Avasys for the V30, there's a big warning link that takes you to a workaround for Mandriva and Debian, so I'm guessing this might affect Ubuntu as well.  In fact, the workaround involves modifying some udev rules.  Maybe give it a shot?

[http://avasys.jp/eng/linux_driver/faq/id000623.php]("http://avasys.jp/eng/linux_driver/faq/id000623.php")

---

### Post by BB2008 on 2009-12-29
Trying to warm up this seemingly dead thread....

So, I have a epson V30 as well, and i am seeing the same issues on my Karmic Koala installation...I can run my scanner fine as sudo, but not as a regular user. That is obviously not healthy.

This started only after I upgraded to 9.10 from 9.04 though, it was working fine before that. So did anyone on this thread figure this out? Please let me know...

---

### Post by shortmort37 on 2009-12-29
Sorry, no help with upgrade details.  I'm a first time Ubuntu user, 9.10 -- all I can tell you is I installed the Avasys drivers, and it worked out of the box:

[http://ubuntuforums.org/showthread.php?t=1328861](http://ubuntuforums.org/showthread.php?t=1328861)

Dan

---

### Post by ellgor on 2009-12-30
Hi,

Try Imagescan from the Avasys site, download the deb package and install with gdebi, may take a reboot, then click on the Imagescan icon and you away.

Regards, Ellgor.

---

