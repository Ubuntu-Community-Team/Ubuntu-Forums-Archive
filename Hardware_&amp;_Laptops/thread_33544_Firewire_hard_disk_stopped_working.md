---
title: "Firewire hard disk stopped working"
date: 2005-05-11
forum: Hardware &amp; Laptops
---

### Post by jon21 on 2005-05-11
My Seagate external firewire hard disk was working fine (just plugged it in and it worked).  Now it is not recognized at all.

I have modified my system recently, including installing nVidia drivers and altering display settings, but nothing seemingly related to the disks or firewire.

dmesg shows:
ieee1394: raw1394: /dev/raw1394 device initialized
ohci1394: fw-host0: SelfID received, but NodeID invalid (probably new bus reset occurred): 0800FFC0

---

### Post by Niiico2 on 2005-05-15
I have exactly the same problem !

I always update my system when the icon asks it in the system tray. I think there was a update that created the problem, but which one ? and how to remove it... that's the question...

---

### Post by Niiico2 on 2005-05-16
Now, i have 3 firewire i cannot acces, ie, lots of important data i cannot acces...

Anyone has an answer ?

---

### Post by Emerick on 2005-05-17
Same problem for me i guess.
Here is the message that show up in /var/log/messages

```
May 11 21:33:00 localhost ieee1394.agent[2097]: ... no drivers for IEEE1394 product 0x/0x/0x
May 11 21:33:00 localhost ieee1394.agent[2105]: ... no drivers for IEEE1394 product 0x/0x/0x 
```

---

