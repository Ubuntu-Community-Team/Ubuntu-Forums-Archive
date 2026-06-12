---
title: "HP pavillion dv9428nr"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by cl0ckwork on 2008-01-18
hey guys, noob to linux sorry if this has been here before, maby im just not understanding something.
i have the 7.04 cd that ubuntu shipped to me because at the time i had a slow internet connection so i couldnt download the ISO.
i have an HP pavillion dv9428nr laptop, all the goodies, AMD capable of running 64bit(do i need a specific ISO for this?)
when i boot from the cd it shows the boot screen, start/install ubuntu, start in safe grafics mode and such
but when i go to install it, it gives me an error in locating a hardware driver in lib/firmware/bcm43xx_microcode.fw
any help at all would be appreciated

---

### Post by pytheas22 on 2008-01-18
It's referring to the driver for a Broadcom wireless card, which uses non-free firmware which I think is still not shipped with Ubuntu.  However you can easily install it: open Synaptic (System>>Administration>>Synaptic Package Manager) and search for fwcutter.  Install the package that comes up; after (or maybe during; I forget) the installation, it should automatically ask you something like "do you want to download the non-free firmware?"  Click yes, reboot and everything should be great.

EDIT: I was assuming that you could get the system booted and things.  If not, give a more precise example of what happens after you select "Start or Install Ubuntu" and hopefully we'll be able to figure out what's wrong.
```

do i need a specific ISO for this?
```

Yes, you would need to burn the 64-bit version of the ISO image.  But you can use the 32-bit just fine; you'll just be missing out on the advantages of a 64-bit processor, which still aren't earth-shattering or anything.

---

### Post by cl0ckwork on 2008-01-18
i have looked at some other threads when i got up this morning and maby something is wrong with my graphics driver because is doesnt show a desktop screen after it says it loads the kernal and drivers after i click the start/install ubuntu from the first boot screen.
all i get is a bunch of vertical lines.
would entering the "noapic noirqdebug" possibly solve this problem?

---

### Post by Ayuthia on 2008-01-18
> **cl0ckwork said:**
> i have looked at some other threads when i got up this morning and maby something is wrong with my graphics driver because is doesnt show a desktop screen after it says it loads the kernal and drivers after i click the start/install ubuntu from the first boot screen.
all i get is a bunch of vertical lines.
would entering the "noapic noirqdebug" possibly solve this problem?

That should help it work.  At least that is what I use, but I have a dv6338se.  Here is a link from someone else getting started with a dv9428nr:
[http://ubuntuforums.org/showthread.php?t=531401](http://ubuntuforums.org/showthread.php?t=531401)

---

