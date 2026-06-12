---
title: "Wacom Bamboo Pad not detected"
date: 2013-10-30
forum: Hardware
---

### Post by chris.wallace on 2013-10-30
1I am running ubuntu 13.04.  I have a new Wacom Bamboo Pad, that is "not detected" when I do settings -> Wacom Tablet.  I have googled, and possibly I need a newer driver, but I cannot see how to install one without upgrading to 13.10 which I cannot do (this is a work machine, and although I have sudo rights, upgrading the distribution would be viewed badly).  Any advice appreciated!  Potentially relevant information:

```
$ uname -r -v -m
3.8.0-33-generic #48-Ubuntu SMP Wed Oct 23 09:16:58 UTC 2013 x86_64
$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 001 Device 004: ID 046d:c078 Logitech, Inc. 
Bus 002 Device 003: ID 0bda:0181 Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 056a:0318 Wacom Co., Ltd 
$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Natural® Ergonomic Keyboard 4000    id=9    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB LaserStream(TM) Mouse          id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Microsoft Natural® Ergonomic Keyboard 4000    id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=12    [slave  keyboard (3)]
$ lsmod | grep -i wacom
$ dpkg --list | grep -i wacom
ii  libwacom-common                           0.7-1                                                                  all          Wacom model feature query library (common files)
ii  libwacom2:amd64                           0.7-1                                                                  amd64        Wacom model feature query library
ii  xserver-xorg-input-wacom                  1:0.19.0-0ubuntu1                                                      amd64        X.Org X server -- Wacom input driver

```

---

### Post by Favux on 2013-10-30
Hi Chris,

Welcome to Ubuntu forums!


To get a working Wacom kernel driver/module in 12.04 you use input-wacom:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Input-wacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Input-wacom)

To update your X driver xf86-input-wacom:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom)

The [BambooPT HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110408") also describes updating the drivers.

I don't think the Bamboo Pad is supported yet by input-wacom.  In order to tell run **lsusb** in a termnal and post the Wacom line.  That will give the Product ID for the tablet so we'll be able to determine if it is supported.


Ordinarily compiling and installing the drivers is fairly simple.  Unfortunately Precise 12.04 comes with a couple of caveats.  The first one is you'll need to apply the frankenserver patch to xf86-input-wacom as discussed in the HOW TO.  That isn't mentioned on the wiki page.  12.04 has a hybrid X Server and without the patch plugging the tablet in will crash the system.

A new issue has appeared with some recent point releases of 12.04, namely 12.04.2 and 12.04.3.  So to discover you 12.04 minor version in a terminal run:
```
cat /etc/issue
```

---

### Post by chris.wallace on 2013-10-30
1Thank you for the detailed reply.

First, I am running 13.04, not 12.04, do the same instructions apply?  (I will read the links anyhow).

lsusb gives
```
Bus 002 Device 004: ID 056a:0318 Wacom Co., Ltd
```

cat /etc/issue gives
```
Ubuntu 13.04 \n \l
```

---

### Post by Favux on 2013-10-30
With 13.04 should be golden.  None of the 12.04 issues.  :)

Alright looking through the input-wacom announcements and the input-wacom git browser I don't see anything for the Product ID 0318.  I didn't check the kernel's linux input mailing list, which is where patches to the Wacom kernel driver are submitted first.  You may want to post to [linuxwacom-discuss]("https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss") and ask when support is anticipated.  I see [one request]("http://sourceforge.net/p/linuxwacom/mailman/message/31410322/") about Bamboo Pad wireless support, but for the 0319, from a few of weeks ago:    No response which is unusual.

**As an aside, you can ignore this:**  If you look at the message as html (that could be why no response, folks didn't see the message?) you see he suggests code that might support the Pad in input-wacom.  That's something you can try.  Making a stab at the code and compiling input-wacom and testing.  No guarentee and takes time.  But back in the day before the current level of developer support sometimes it was the only way to get something "working" in a reasonable amount of time. 

The Linux Wacom wiki:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page)

---

