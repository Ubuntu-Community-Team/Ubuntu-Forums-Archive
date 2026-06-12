---
title: "Connecting to cisco device over /dev/ttyS0"
date: 2008-10-17
forum: Hardware
---

### Post by JWedrowycz on 2008-10-17
Hi everybody,

My problem looks like this: after establishing the connection with minicom, cu, cutecom or gtkterm my laptop (IBM T42 in the dockstation II) sends every 8 seconds "AT" string and every 8 seconds "^Z" string.

Looks like that:
...

Cisco#AT
Translating "AT"
% Unknown command or computer name, or unable to find computer address
Cisco#^Z
Cisco#
Cisco#AT
Translating "AT"
% Unknown command or computer name, or unable to find computer address
Cisco#^Z
Cisco#
Cisco#AT
...

In that situation only cutecom allows me to work somehow (for example write an enable pass for privilaged mode). So the problem lies in configuration of the Ubuntu system 8.04 2.6.24-21.42-generic which I am using.
I would be very glad for any suggestions.

Thanks in advance,
JWedrowycz

---

