---
title: "Usb ports 3.0 and 2.0 doesn't work or pop up"
date: 2020-01-08
forum: Hardware
---

### Post by cudder-felix on 2020-01-08
Hi Community, I need help with my system. I use a Dell Inspiron 5539. I installed Ubuntu on the console, but my ports stopped working for a while now. My two USB2.0 ports are totally out(They don't even charge my device when I plug in). But my USB 3.0 charges my phone, but Ubuntu doesn't recognize or Pop-up when connected. I really need help with this issue. 
Best Regards!

---

### Post by Autodave on 2020-01-08
Sounds like a hardware issue: something failed.  However, you may want to try this: I have seen it fix a lot of laptops with new / weird problems.

Power down. Disconnect EVERY cable.  Remove battery.  Leave battery out for 10 minutes.  Install battery and power cord only.  Power up.  See if it works now.

---

### Post by Yellow Pasque on 2020-01-08
> Dell Inspiron 5539
Do you mean 55**93**? Googling 5539 doesn't come up with much useful information.
Are you updated to the latest BIOS version?
Can we see more info?
```
sudo lsusb -tv
```

---

