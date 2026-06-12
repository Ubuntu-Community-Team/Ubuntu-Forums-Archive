---
title: "Logging an External RS-232 Port?"
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by mac57 on 2006-10-20
This is an odd one - not really sure where to post it, so I chose the hardware area. 

I am trying to use my Ubuntu PC to monitor and log the ASCII transactions on an RS-232 link. My PC has external RS-232 connectors, and so I have the right hardware.

Is there a way to figure out what the tty device associated with the physical RS-232 connectors is? Once I have figured that out, can I somehow get Ubuntu to log everything that comes in on that tty to either a file or even better to an xterm (that way you can see it in real time AND log it using standard xterm logging)?

The application here is to get message traces from an old voicemail system running RS-232 SMDI signalling, so that we can build an equivalent interface on a new PC-based system. Thanks!

---

### Post by linux2512 on 2006-10-20
You could try tailing the /var/log/kern.log as you plug the device to see what the driver reports.  Usually it'll tell you which tty device is associated.

Depending on the type of device/driver you may be able to just cat the attached device or use minicom.

Hope this helps

---

### Post by mac57 on 2006-10-20
Thanks, that was helpful. I should have thought of checking the logs myself! Cheers.

---

