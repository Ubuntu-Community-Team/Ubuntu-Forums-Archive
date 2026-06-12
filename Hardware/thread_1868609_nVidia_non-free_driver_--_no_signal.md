---
title: "nVidia non-free driver -- no signal"
date: 2011-10-24
forum: Hardware
---

### Post by moonguide on 2011-10-24
I upgraded a Sony Vaio VGC-RB40 running ubuntu 10.04 with an nVidia Quadro NVS 295 PCIe card. Once installed the display came up and looked nice and crisp. However foobilliard ran very slowly. I realized I had not checked to see if an nVidia driver was in use. Of course, since I hadn't installed one, it wasn't in use. I clicked on System > Administration > Hardware Drivers. The Hardware Drivers window reported that no proprietary drivers were installed and gave me three options: nVidia accelerated graphics driver (version 173), (version 96), and (version current). [Recommended] was listed next to (version current) so I selected the current version and clicked on Activate. After about 1/2 hour of downloading the driver installed and I was notified of the need to restart the system. 

When I rebooted I saw the following: a blank screen followed by a largish underscore cursor about an inch and a quarter down from the top of the monitor followed by a screen with a normal sized cursor at the top of the monitor. The Ubuntu dots appeared, then a login prompt flashed by. Then the screen went blank and then the monitor reported no signal.

There was no visual response to the mouse or keyboard so I power cycled the machine. The only difference to what I said in the preceding paragraph was the appearance of the Sony Vaio splash screen before the largish cursor screen.

I rebooted the machine with the Ubuntu 10.04 install CD in try out mode and the screen appears as it did before the attempted driver installation.

How do I fix this? Do I do something to uninstall the nVidia driver while booted from the CD? 

If that doesn't work and if I pull the card and restart with the monitor connected to the built-in VGA video, is there some way I can do something from there?

Any other suggestions are welcome, including whether or not I should experiment with driver versions 173 and/or 96.

Thanks.

---

### Post by moonguide on 2011-10-25
After much Googling I found several threads on various forums that offered numerous ways to fix this that didn't work for them or me. The last thing I read as a solution was to re-install Ubuntu.

One point in favor of this is that I did not have the card when I first installed the OS. I'm in the process of backing up now and will re-install the card and re-install the OS. Then I'll try upgrading to the proprietary drivers before doing anything else.

---

### Post by moonguide on 2011-10-28
Screwy solution: Use a DVI -> VGA adapter and connect to the monitor's VGA port. 

The non-free driver loads just fine.

I also tried connecting a VGA monitor that way and using the DVI-D cable on the second port to connect a DVI-D monitor. The nVidia driver can see both monitors but won't send a signal to through the DVI cable on port 2.

If anyone has any ideas about why it doesn't work to connect using DVI I'd appreciate hearing them.

---

