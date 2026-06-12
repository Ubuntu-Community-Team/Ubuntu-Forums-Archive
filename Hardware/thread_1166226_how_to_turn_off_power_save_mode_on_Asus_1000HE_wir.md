---
title: "how to turn off power save mode on Asus 1000HE wireless?"
date: 2009-05-21
forum: Hardware
---

### Post by trherald on 2009-05-21
does anyone know how to turn off the powersave mode on the wireless LAN for an ASUS 1000HE?  

In Windows, the option can be changed under the NIC advanced properties tab, but I don't see anything comparable in Ubuntu which will let me do the same thing.

thanks for the help!

---

### Post by trherald on 2009-05-24
problem solved.....iwconfig is the answer

first, if you use iwconfig in a command window you'll see a listing which should include 'wlan0'.  Within that group, you should see a line 'Power Management', which in my case is 'off' (that's the value I wanted to see).

if, however, yours isn't off, you can use "iwconfig wlan0 power off" to turn off the power save mode.

The reason for doing this is so that the wireless adapter doesn't try to use power saving and disconnect the connection while you're using it!  Seems to result in a much more stable connection.

---

