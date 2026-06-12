---
title: "Installing ATI Raedon Driver - Terminology"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by MaindotC on 2009-04-30
From the [Open Source ATI Driver wiki](https://help.ubuntu.com/community/RadeonDriver):
> IT HAS TO BE ati and NOT radeon or fglrx. The "ati" driver is a wrapper that will load the "radeon" driver if possible.

What is a "wrapper"?

---

### Post by Mark Phelps on 2009-04-30
It's a generic driver shell that loads one of several different video drivers, depending on the results of hardware detection.  The radeon driver is only one of the drivers it would select.

---

### Post by MaindotC on 2009-04-30
Thanks - I think that makes sense.  How do I determine what Options I can enter in xorg.conf to properly configure my x850 video card or is there a configuration for the card already listed somehwere?

---

### Post by MaindotC on 2009-05-01
bump - any help configuring for x850 would be appreciated.

---

### Post by Mark Phelps on 2009-05-01
Try "man radeon" (presuming you're using the open source driver).  It will show LOTS of options you can use.

---

### Post by MaindotC on 2009-05-01
I'm aware of the man page, but the [Open Source ATI driver wiki](https://help.ubuntu.com/community/RadeonDriver) states:
> From Ubuntu 7.10 and onwards, the driver and server autodetect most settings. You can often just take away your xorg.conf and it will run fine.
So were are the configurations being stored if they're not in xorg.conf?

---

