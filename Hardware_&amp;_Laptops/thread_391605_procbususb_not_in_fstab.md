---
title: "procbususb not in fstab?"
date: 2007-03-23
forum: Hardware &amp; Laptops
---

### Post by copymaster on 2007-03-23
Hi everybody,
i have a strange prob. 
i tried virtualbox and it works for me faster as vmware server....
the only thing is that i am unable to use usb devices (i have the binary, not the GPL version) for private use it is free...

in my /etc/fstab there are only proc and the harddisks mounted and the cdrom of course. but when i make a mount it tells me that procbususb is also mounted ???
how is procbususb mounted when it's not in the fstab????

the prob is, that virtualbox will use the usbfs and therefor this usbfs must have the right rights for the user.. but i can't find the config, where procbususb is mounted. its not /etc/fstab...


if i manually mount /proc/bus/usb, the usb controller freezes, when i start virtualbox and within the guest (its a vista and a linux) i am not able to use usb sticks, usb-hatrddisks and so on.

PLEASE HELP!!!

Can anybody tell me how to configure usbfs or virtualbox to use my usb-devices?

---

### Post by dfreer on 2007-03-23
At least on my system, procbususb is mounted in /etc/**mtab**. :) hope this helps

---

### Post by copymaster on 2007-03-23
****! :)  sorry ....

---

### Post by dfreer on 2007-03-23
lol no worries!

---

