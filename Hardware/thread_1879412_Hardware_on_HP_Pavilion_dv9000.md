---
title: "Hardware on HP Pavilion dv9000"
date: 2011-11-11
forum: Hardware
---

### Post by bold.unicorn on 2011-11-11
Hello,

Sorry for my english and knowledges in Linux sphere;

I have next problem: my laptop HP Pavilion dv9000 have a camera and wireless adapter by Broadcom that havent's drivers in list of aviable drivers. Who can tell me about algorhytm to install this drivers? First goal is working webcam in skype. Thx.

PS I think, you will need in my lsusb to analyse them:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ca:1870 Ricoh Co., Ltd Webcam 1000
Bus 002 Device 004: ID 09da:054f A4 Tech Co., Ltd 


If you need in more information, please inform me. If it have value - I use KDE (Oneric)

---

### Post by wman on 2011-11-12
My laptop is hp Pavilion  g4-1057tu ,oneric(gnome),but the webcom and wireless worked normally~Maybe you can read this  page :[http://ubuntu-tweak.com/source/xorg-edgers-ppa/](http://ubuntu-tweak.com/source/xorg-edgers-ppa/)

---

### Post by northd_tech on 2011-11-12
My laptop is a HP DV98xx series, also with a webcam and Broadcom '4328'/4321AG wireless.

**lsusb** tells me:
> Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 002: ID 064e:a110 Suyin Corp. HP Webcam**
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 18a5:0216  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Also for my working Broadcom wireless:
> **lsmod | egrep 'b4|ssb|wl'**
wl                   1964968  0 
lib80211                6151  2 lib80211_crypt_tkip,wl
If your HP DV9xxx laptop doesn't have a Broadcom wireless (which I really doubt), then let's see the output of a plain old **lsmod** statement instead.

Also, I suspect these are my Webcam driver modules under **lsmod** (although I hardly ever use the Webcam):

> 
Module                  Size  Used by
video                  20623  0 
output                  2503  1 videoAre you using Cheese or Ekiga or something else to activate the Webcam?  I think I have used both, but I recently re-installed Ubuntu and don't appear to have either installed right now to check.

[http://maketecheasier.com/videoconference-linux-and-windows-with-ekiga/2009/08/05](http://maketecheasier.com/videoconference-linux-and-windows-with-ekiga/2009/08/05)

[http://linux.softpedia.com/get/Multimedia/Graphics/Cheese-28762.shtml](http://linux.softpedia.com/get/Multimedia/Graphics/Cheese-28762.shtml)

Here is the Webcam HOWTO (which looks pretty old to me):

[http://tldp.org/HOWTO/html_single/Webcam-HOWTO/](http://tldp.org/HOWTO/html_single/Webcam-HOWTO/)

If you are trying to use Skype, then I would think that wireless internet would be at least (if not more) important as the Webcam.

You can find your wireless interface with this command:

```
sudo lshw -C network
```

---

### Post by northd_tech on 2011-11-12
That Ricoh Webcam 1000 had some issues under Ubuntu Jaunty and Karmic versions, but I found some suggested fixes here:

[http://ubuntuforums.org/showthread.php?t=1266384](http://ubuntuforums.org/showthread.php?t=1266384)  (posts #10, 12 & 13)

[http://ubuntuforums.org/showpost.php?p=9326419&postcount=2](http://ubuntuforums.org/showpost.php?p=9326419&postcount=2)

---

