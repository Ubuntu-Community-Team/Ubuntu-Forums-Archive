---
title: "Modem - No Dial Tone"
date: 2005-11-15
forum: Hardware &amp; Laptops
---

### Post by pizzipie on 2005-11-15
Hi,

I am running Breezy 5.1 on an HP pavillion zt1135 laptop. 

Problem is my modem will not connect. I issued the following commands for debugging:

command: cardctl --> 5 v 16-bit PC Card
                                        function 0: [ready], [req attn]

command: cardctl ident 0 --> Product info: "U.S. Robotics",                      "USR0756-XJ/USRo756-CB"

command:  wvdial --> Internet dialer version 1.54.0
--> Initializing modem.
--> Sending ATZ
ATZ
OK
--> Sending ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> modem initialized
--> Sending ATDT(IP phone number here)
--> Waiting for carrier
ATDT(IP phone number here)
NO DIAL TONE
--> no dial tone
--> disconnecting

I used another laptop on this same phone line and all ok. The HP pavillion was previously running w/ ubuntu 5.04 Hoary and this same modem worked fine.

HELP!! 

Thanks in advance RP.

---

