---
title: "Need to disable two features of apcupsd"
date: 2008-08-26
forum: Hardware
---

### Post by pwn on 2008-08-26
I just bought an APC Back-UPS BR800 and it works perfectly with apcupsd, but I want to disable two of the features because I dont need it. These are:

1. Shut down feature when the UPS battery is out of charge (I use it with a laptop which has its own battery)
2. When the UPS switches to backup, I get a broadcast message in my terminals saying there was a power failure and the UPS is now running on backup.

I looked into apcupsd.conf and I see only options that specific how long after it starts running on backup or how much power left till the system is shut down. I am not sure how to disable that feature completely.

Anyone has any ideas?

---

### Post by pwn on 2008-09-01
#2 is fixed.

Still looking for a way to prevent it from shutting down the PC.

---

### Post by pwn on 2008-09-02
#1 is fixed too.

I was looking into the wrong file.

Incase anyone else is looking to do the same, edit /etc/apcupsd/apccontrol, and comment out WALL (for broadcast messages) and SHUTDOWN lines.

---

### Post by Nathan.Flow on 2010-06-30
> **pwn said:**
> I just bought an APC Back-UPS BR800 and it works perfectly with apcupsd, but I want to disable two of the features because I dont need it. These are:

1. Shut down feature when the UPS battery is out of charge (I use it with a laptop which has its own battery)
2. When the UPS switches to backup, I get a broadcast message in my terminals saying there was a power failure and the UPS is now running on backup.

I looked into apcupsd.conf and I see only options that specific how long after it starts running on backup or how much power left till the system is shut down. I am not sure how to disable that feature completely.

Anyone has any ideas?

are you useing a usb cable, if so can you tell me how you got apbups to work? I keep getting ```
Terminating due to configuration file errors.
```

---

