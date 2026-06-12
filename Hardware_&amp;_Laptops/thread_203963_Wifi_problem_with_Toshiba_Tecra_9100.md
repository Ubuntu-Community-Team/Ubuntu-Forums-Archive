---
title: "Wifi problem with Toshiba Tecra 9100"
date: 2006-06-26
forum: Hardware &amp; Laptops
---

### Post by bibog on 2006-06-26
Hi,

first time I installed Ubuntu 5.1 from a CD, everything went very good. My Wifi onboard device has been detected and installed. 

I then upgraded online to 6.06, I had no error messages, but my Wifi interface is not working anymore.


When booting, if I choose from the boot menu the older linux kernel. Wifi works again...

Is there a known driver problem with this last version.
Thanks.
Bibo.

---

### Post by jml on 2006-06-26
The short answer is yes.  If you take a look at the wireless sub-forum, you will see many references to wireless set-ups breaking when people upgraded from 5.10 to 6.06.  No one cause for the problem, it seems to be multiple issues.

Joe

---

### Post by fredex on 2006-07-17
Has anyone figured out how to get wireless networking to work on dapper (6.06) on a tecra 9100?

I've just done a fresh first-time install on an old Tecra 9100. Ubuntu claims to find the wireless hardware. I can use the network manager to configure it and to enable it. After it displays the busybox for a while it comes back and says it is active. If I then do "/sbin/ifconfig" it shows that the wireless connection has been assigned an IPV6 address, but no IPV4 address. I can't seem to ping or telnet or browse web through that connection.

FWIW, manually configuring it in windows (XP) using the same WEP keys it works fine, so the hardware is working.

Anybody got a hint?

Should I perhaps just blow it away and install 5.0x instead?

---

### Post by Gtaylor on 2006-07-29
Check my Tecra A4 page under "Restoring USB/Network". This should be applicable to you too. You need to upgrade your bios in the short.

[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaTecraA4](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaTecraA4)

---

