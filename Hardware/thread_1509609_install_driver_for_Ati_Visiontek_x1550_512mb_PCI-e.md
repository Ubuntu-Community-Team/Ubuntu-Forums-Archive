---
title: "install driver for Ati Visiontek x1550 512mb PCI-e on lucid"
date: 2010-06-14
forum: Hardware
---

### Post by ghoststar on 2010-06-14
Hi, 

I've tried installing catalyst[in hopes it would recognize my graph-card] and got the following error: 

> There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.  No ATI graphics driver is installed, or the ATI driver is not functioning properly.
 Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.
Which, started this quest to get my card installed properly.


So, i have no idea where to start off at all. 


When I call > lspci -nn | grep VGA

**02:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series] [1002:7183]**


This is from a fresh Lucid install.



Any help/support would be greatly appreciated.


--

Jahvid

---

### Post by Virtual62 on 2010-09-03
im having the exact same issues as well, however i have the AGP card version of the X1550 series

if there is any way to resolve this, it would be much appreciated :)

---

### Post by hsoulen on 2010-09-03
Hi Guys,

Not 100% positive as I do not have an ATI card but I am pretty sure that the latest ATI proprietary drivers (fglrx) do not support your card.

But there is hope! You can try the following:


[LIST=1]
[*]Download an older version of the driver that supports your card and use these instructions: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[*]Use the OpenSource alternatives (which I hear are pretty awesome): [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[/LIST]

Good luck!

Hank

---

### Post by Virtual62 on 2010-09-03
ok i tried the option of installing an older driver

the issue is that my current xorg version is 7.6 and the driver only works uptill 7.4

is there a way of downgrading the current xorg version?

---

### Post by hsoulen on 2010-09-06
> **Virtual62 said:**
> ok i tried the option of installing an older driver

the issue is that my current xorg version is 7.6 and the driver only works uptill 7.4

is there a way of downgrading the current xorg version?

Technically "yes" you can (see this thread: [http://ubuntuforums.org/showthread.php?t=1377819](http://ubuntuforums.org/showthread.php?t=1377819)) but if you look through that thread (attempted due to running in VBox) you'll see that it is probably more trouble than it is worth.

Just my two cents but running the Open Source driver with the card you have will probably give you 80-90% of the functionality and performance of an older proprietary driver, alternatively you can get a new/used pci-e card with better performance that supports the most recent proprietary driver for VERY cheap... I know this is not always and option if you are a student etc. on a fixed budget but just looking at newegg under Graphics Cards yields a bunch of <$80 (some unde $50) cards that will smoke your current 1550 and will work brilliantly with the newer drivers.

I am not a huge NVidia fanboy but in my experience their support for Linux is a bit better on the proprietary driver side than AMD/ATI, that said AMD/ATI does a lot more in the way of providing support for the Open Source development of drivers for their products.

Hope this helps.

Hank

---

