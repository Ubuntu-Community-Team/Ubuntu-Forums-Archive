---
title: "USB 1TB drive not accessible"
date: 2018-02-14
forum: Hardware
---

### Post by nauttboy2 on 2018-02-14
In desktop of lubuntu 14.04 on SMB Orangepi PC, as I plug in my usb drive it immediately recognized it but error getting it to mount.  I will have to try it again when I get home and upload pic or describe the error.
Is there something I need to know prior to plugging/installing it?

---

### Post by TheFu on 2018-02-14
Did it ever work?
How is it formatted?
How many partitions does it have?
Do you have udev rules to have it mount somewhere or not?
Is autofs setup?

Can you manually mount it? If not, what are those errors?

Did you check the system logs?  Issues normally show up there.  syslog and message/dmesg will show these.

---

### Post by nauttboy2 on 2018-02-15
Yes it works if I plug it in windows pc.
Here is what I'm doing.  This drive is new I use for network drive files. I am planning to have it connect to my pi.  Install surveillance software in my pi and have it record to that ext drive since my pi is only 32gb.  I rather have my pi on all the time rather than my pc so it could record.  Still need to do that again to capture the error. Been buys. I have several thread open, I should just start one at a time.

---

### Post by TheFu on 2018-02-15
And all the other questions?  Working in Windows **is** something, but that removes 1 aspect, not all the others.  Some USB drive controllers only work in Windows.
 
There's a reason a PI doesn't support SATA - not enough internal data lanes.  You might want an Odroid instead or an APU2 for a little more industrial solution and both use 10W or less and have SATA support.

But having a Pi to try things out isn't a total waste.

The other questions asked above?  If you open different threads for the same question, the mods will not be happy.

---

