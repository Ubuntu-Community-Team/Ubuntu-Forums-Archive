---
title: "Broadcom 4311 + ndiswrapper Not Connecting to WPA/WPA2 Networks [Solved]"
date: 2009-04-02
forum: Hardware
---

### Post by c_07 on 2009-04-02
Hello all,

After upgrading to Ubuntu 9.04 Beta, my laptop would no longer connect to WPA/WPA2 encrypted wireless networks, although it would still connect to unprotected networks without a hitch. In 8.10, the connection would sometimes stall, but I could always get it to connect -- unfortunately, after upgrading it failed completely.

On the second day of searching, I found the following thread:

[http://ubuntuforums.org/showthread.php?t=896713]("http://ubuntuforums.org/showthread.php?t=896713")

The solution presented there is more of a work-around (i.e., use restricted drivers), but I am posting the link just in case someone with similar hardware experiences the same behavior with ndiswrapper. Disabling ndiswrapper, downloading the latest drivers from Broadcom, and enabling them as the article describs fixed the problem for me; I am assuming this is probably because it enables you to use the latest drivers from Broadcom, instead of the default ones you get with the hardware.

---

