---
title: "USB 3.0 does not detect devices"
date: 2011-04-18
forum: Hardware
---

### Post by rkwellstead on 2011-04-18
I have three computers with an add-on USB 3.0 card (NEC chipset) and all of them exhibit the same odd behaviour. None of them detects any USB 3.0 device - I have to either start the computer with the USB 3.0 device already plugged in, or unload the xhci module before plugging in a device and reloading the module to get it to work.

Once working, it is fantastic, with no problems. I get faster transfers to hard disks and a Kingston DT Ultimate flash drive than in Windows 7 (also installed on one of the machines).

I cannot find anyone with the same problems, and no information that seems relevant when searching for xhci problems in Linux in general.

Has anyone else got the same problems?

---

### Post by jupy on 2011-06-28
I have a problem alike. I've just bought Lenovo Y470 notebook. It has two USB 3.0 ports. Ubuntu 11.04 can't see them. 

Can anybody help me? Tx.

---

### Post by sabotatore on 2011-07-29
I have the same problem with my y470..  Does anybody resolve it?

---

### Post by TheMiz on 2011-08-16
I just got my lenovo y470, and I am having the same problem with it recognizing the USB3.0 port when I plug a device into it.

Also I am having a major headache with the nvidia drivers (Off topic, but it is bad).

---

### Post by TheMiz on 2011-08-16
just found this:


> Also, the 2 usb 3.0 ports on the left side of the ideapad y470 do not  work "out of the box" with Red Hat Linux. (Either fedora or CentOS 6).  To fix this in Red Hat:
 
create a file: /etc/sysconfig/modules/xhci_hcd.modules



```

#!/bin/sh
echo -n "Loading xhci_hcd module..."
if /sbin/modprobe xhci_hcd
then
        echo "SUCCESS"
else
        echo "FAILURE"
fi

```
chmod 755 /etc/sysconfig/modules/xhci_hcd.modules
 
This will load the module for usb 3.0 support at each boot in a red hat type OS. Not sure about other distros.
 
&#65279;xhci_hcd&#65279;  is kind of experimental in Linux and it has some bugs. So sometimes you  may to may need to rmmod it. Definately want to do that before  hibernate or suspend operation. Then modprobe it again as you wake up.  So with this hack the usb 3.0 ports are good to go. [IMG]http://lnv.i.lithium.com/i/smilies/16x16_smiley-happy.gif[/IMG]
I am not really brave enough to try it, and I don't even understand everything he is saying about xhci_hcd.

---

