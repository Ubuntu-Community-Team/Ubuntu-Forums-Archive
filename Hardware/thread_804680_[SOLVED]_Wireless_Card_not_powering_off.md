---
title: "[SOLVED] Wireless Card not powering off"
date: 2008-05-23
forum: Hardware
---

### Post by boltorg on 2008-05-23
My setup:

Laptop - Inspiron 2500
Wifi Card - PCMCIA DWL-G630 Rev.C1
Distro - Xubuntu 8.04 with some Edubuntu Add-ons - running RT kernel - fully updated

Problem:

Upon shutting the laptop off the console initially gave network manager errors, I've fixed that per this thread.
[Link to Thread]("http://ubuntuforums.org/showthread.php?t=784857&highlight=nm_signal_handler+caught+15")

This did not fix the issue of the PCMCIA wifi card powering completely off.  The laptop is completely off but the wifi card has one LED still lit.  Upon rebooting the laptop and logging in the kernel doesn't even see the wifi card. lspci or lspcmcia doesn't yield results about my card either.  The only way to get the card to be recognized again is to turn off the laptop, remove the battery, remove the power source, then reboot.

---

### Post by boltorg on 2008-05-23
Making some headway on this issue, thanks to Nate Berry at
[http://planet.lilug.org/](http://planet.lilug.org/)

> Shutting Down
Getting the wireless working introduced a new problem shutting down. Shutting down normally actually brought me to a black screen after the process, but didn&#8217;t shut the laptop OFF actually. To shut off all the way I&#8217;d have to hold in the power button for 5 seconds. I found that turning off the PCMCIA slot first allows Ubuntu to shut down completly. Just have to add &#8220;/sbin/pccardctl eject&#8221; to the shutdown scripts: I wrote a little bash script
[QUOTE]#!/bin/bash
/sbin/pccardctl eject
and saved it in /etc/init.d (and chmod to 755 so its executable)
Then in /etc/rc0.d, I made a symlink to my script named S22ejectcard
with ln -s ../init.d/ejectcard S22ejectcard[/QUOTE]

This works for completely shutting down the machine.  It does not work for restarting the machine as the pcmcia card still "hangs" on to power after the reboot.

Does a restart command go through a different rc level other than 0?

---

### Post by boltorg on 2008-05-30
BTW I like talking to myself in my own thread.

Tried downgrading to 7.10 - wireless card not detected.
8.04 uses the ath_pci driver.

I also notated that on installation a dialog prompted to exclude ports on dell laptops, dealing with the pcmcia slots.

I havn't found anything about an inspiron 2500's parameters.

Any ideas would be welcome...

---

### Post by DellCA on 2008-05-30
Yes, init 0 is shutdown, while init 6 is restart, so you probably just need to add the script to the rc6.d directory as well.

I use a 3com 3c577 card in my notebook running Gentoo, and do not have this problem so I am not sure what the actual problem is.  However, it sounds to me like something with either the PCMCIA card itself, or the drivers for it (kernel and/or module configuration).

Hopefully this helps.

Larry
Dell Customer Advocate

---

### Post by boltorg on 2008-06-06
Linking to the script in rc6.d worked a champ!

Thanks!

---

