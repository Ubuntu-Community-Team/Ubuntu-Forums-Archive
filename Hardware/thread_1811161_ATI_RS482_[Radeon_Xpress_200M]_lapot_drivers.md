---
title: "ATI RS482 [Radeon Xpress 200M] lapot drivers"
date: 2011-07-24
forum: Hardware
---

### Post by TheKeyMaker on 2011-07-24
Having trouble with a acer aspire 5100 laptop ATI graphics.

```

lspci | grep -i vga
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]

```

I would like to get a game running on it, and am trying to install proprietary drivers, but I don't think this card supports any.

Is this the case?

The additional drivers menu also doesn't give me anything.

---

### Post by snafu006 on 2011-07-24
> **TheKeyMaker said:**
> Having trouble with a acer aspire 5100 laptop ATI graphics.

```

lspci | grep -i vga
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]

```I would like to get a game running on it, and am trying to install proprietary drivers, but I don't think this card supports any.

Is this the case?

The additional drivers menu also doesn't give me anything.


The card is not supported any more by ati you need to download the drivers from here.

[http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers](http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers)

But they are a long way off from the ati drivers i have the same card and on glxgears i only get 60 fps the only way to get full speed from the card is to downgrade to ubuntu 8.04 and on there i get 800+ fps.

So all n all we are ^&%$

---

### Post by .... on 2011-07-25
> i only get 60 fps 
First, glxgears is not a benchmark. Second, 60fps means video sync is activated and your display is running at 60Hz.

> and am trying to install proprietary drivers
Make sure you completely purge any proprietary driver install: [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx)
After that, install the drivers from xorg-edgers: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

