---
title: "gatttool and hcitool on Linux"
date: 2014-03-22
forum: Hardware
---

### Post by Valeh on 2014-03-22
Hi.
I'm trying to connect to a device using gatttool on Linux. I run hcitool lescan to get the device MAC address, and then gatttool -i hci1 -b <macaddr> -t random -I. Then I type connect.  I see [CON] as expected, but the problem is that it disappears  automatically after about 1s, with no error messages. I have been  searching for hours, but I don't see why that is so?   Note: I have run hcitool lecc before running gatttool one time just to try it, but it seems to me that since then, gatttool connection is not working properly anymore (unexpected disconnection as explained above). Is it because I have used hcitool lecc? If yes, is there a way to "undo" it?

---

