---
title: "Verizon wireless Novatel USB 760 support &lt;=== HELP!"
date: 2009-03-20
forum: Hardware
---

### Post by fcbarnard on 2009-03-20
I am trying to setup my wireless USB modem (760) from verizon on my laptop running ubuntu 8.10. The current kernel that I am running is 2.6.27-11-generic. During my search I noticed that once the usb modem driver is detected and shows up in /dev as /dev/ttyACM0 or something similar it isn't a difficult process to set it up. However right now, my laptop doesn't pick up the modem.

My /dev before and after picture is as follows:

1a2
> after
6a8
> cdrom1
315a318
> scd1
323a327,328
> sdc
> sdc1
328a334,335
> sg3
> sg4
333a341
> sr1
678a687,691
> usbdev5.3_ep00
> usbdev5.3_ep06
> usbdev5.3_ep08
> usbdev5.3_ep85
> usbdev5.3_ep87

Any ideas on how to fix this. Do I have to roll a new kernel with USB modem support. If so how do I do that. Any support would be appreciated. I will use continue to support Linux or die trying!

---

### Post by linuxloner on 2010-02-03
Did you ever find a solution to this problem?  I'm trying to help a friend with the same problem.  We install the hardware driver shown under the "SYSTEM>ADMINISTRATION>HARDWARE DRIVERS" to no avail, then we tried to install the microsoft software that came installed on the device under WINE.  it began consuming resources so i "forced quit" the install, then....all of a sudden it began to work!  we surfed around using the modem for a few minutes, then i restarted ubuntu to see if it would re-recognize the modem.  I hasn't worked since.  I hope we can find a solution as i hate to see someone go back to windblows!

---

