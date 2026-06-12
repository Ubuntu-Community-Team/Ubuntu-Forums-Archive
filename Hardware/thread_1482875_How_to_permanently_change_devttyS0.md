---
title: "How to permanently change /dev/ttyS0"
date: 2010-05-14
forum: Hardware
---

### Post by jazzgossen on 2010-05-14
I have a GPS device that can only be configured to connect to a serial port (/dev/ttyS*). 

I don't have any true serial ports on my computer, so I'm using a serial-to-USB adapter and have removed /dev/ttyS0 and added a symlink to /dev/ttyUSB0 instead. 

This works well, but every time I reboot, the symlink is gone and /dev/ttyS0 is back. 

Is there a way to make this change permanent?

---

### Post by jocko on 2010-05-14
You could probably change whatever boot script that sets up the /dev/ttyS0 in the first place to make the link instead, but I have no idea how to do that.
So I guess you could set up a script to do remove /dev/ttyS0 and create the link during boot.
Try putting something like this in your /etc/rc.local:
```
rm /dev/ttyS0
ln -s /dev/ttyUSB0 /dev/ttyS0
```

---

