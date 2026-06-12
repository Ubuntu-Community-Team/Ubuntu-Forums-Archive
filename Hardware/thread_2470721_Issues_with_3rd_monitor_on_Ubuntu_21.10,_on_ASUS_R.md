---
title: "Issues with 3rd monitor on Ubuntu 21.10, on ASUS ROG Strix gaming laptop"
date: 2022-01-08
forum: Hardware
---

### Post by Goatvirus on 2022-01-08
i have this problem:  i can see a 2nd monitor just fine, if it's plugged into the HDMI port on my ASUS laptop.  however, i really need a 3rd monitor (ie: two external monitors) for what i am doing, and from what i can see, Ubuntu itself does support that!

here's what i am running:

ASUS ROG Strix G513IC 

AMD® Ryzen 7 4800h

Ubuntu 21.10

Linux Kernel 5.13.0-23-generic

Nvidia driver version 470 

i bought an adapter ([https://www.primecables.ca/p-386453-cab-pc-08090-usb-31-type-c-to-vga-male-to-female-adapter-support-1080p](https://www.primecables.ca/p-386453-cab-pc-08090-usb-31-type-c-to-vga-male-to-female-adapter-support-1080p)) so that my USB-C display port is converted to VGA, and have tried two different monitors connected to it, and it doesn't work.  the monitor just acts like "no signal".

and yet, in the 'display settings' config can see that Ubuntu thinks there MIGHT be a 3rd monitor, but when i try to 'apply' a setting where that monitor is marked as 'on', it just reverts back to two again (ie: it turns off the 'on switch' for the 3rd monitor automatically, probably because it can't find the monitor, or can't configure it properly).

i am aware of some of these possible fixes that others have posted:

[https://www.reddit.com/r/ZephyrusG14/comments/hofony/usbc_displayport_under_linux/](https://www.reddit.com/r/ZephyrusG14/comments/hofony/usbc_displayport_under_linux/)

[https://askubuntu.com/questions/1244376/cant-get-internal-and-external-monitor-working-simultaneously-with-20-04-on-lap](https://askubuntu.com/questions/1244376/cant-get-internal-and-external-monitor-working-simultaneously-with-20-04-on-lap)

[https://askubuntu.com/questions/1230924/ubuntu-20-04-does-not-recognize-second-monitor](https://askubuntu.com/questions/1230924/ubuntu-20-04-does-not-recognize-second-monitor)

however, these (and similar articles) don't help in my case because:

- there's no problems with running the laptop monitor and one external monitor

- i have no xorg.conf file

- i have no nvidia-kms file

- i don't think 'power saving' aspect mentioned in some of those fixes is applicable, i have been testing when the monitors weren't blanked by the power saving mode, and my power mode is set to 'Balanced Power', not 'Power Saver'.

i changed nvidia drivers from version 470 to 495 just recently, to see if that would fix it.  nothing else seemed to break, but the monitor issue remained the same.

any ideas?

is the most likely culprit the adaptor itself?  i know it was a fairly cheap one, and i have also read that the exact model/specs of a displayport adaptor can affect whether a 2nd or 3rd monitor will work on ubuntu....

also, suggestions of "running the dGPU as main gpu" (see [https://lab.retarded.farm/zappel/asus-rog-zephyrus-g14/-/wikis/Hardware/Graphics](https://lab.retarded.farm/zappel/asus-rog-zephyrus-g14/-/wikis/Hardware/Graphics) ) - is that my only option left to try?  is that even safe? ;-)

---

### Post by guiverc on 2022-01-08
Also asked at [https://askubuntu.com/questions/1386091/issues-with-3rd-monitor-on-ubuntu-21-10-on-asus-rog-strix-gaming-laptop](https://askubuntu.com/questions/1386091/issues-with-3rd-monitor-on-ubuntu-21-10-on-asus-rog-strix-gaming-laptop)

---

