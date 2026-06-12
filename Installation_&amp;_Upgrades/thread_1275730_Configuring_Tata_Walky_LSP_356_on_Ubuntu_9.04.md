---
title: "Configuring Tata Walky LSP 356 on Ubuntu 9.04"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by hallenr on 2009-09-26
I have been trying hard to try to connect to Internet through my PC with Ubuntu 9.04.

I have installed GNOME PPP,

When trying to connect I get the following in the log file:
> 
&D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DP#777
--> Waiting for carrier.
ATM1L3DP#777
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATM1L3DP#777
--> Waiting for carrier.
ATM1L3DP#777
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATM1L3DP#777
--> Waiting for carrier.
ATM1L3DP#777

I have edited wvdial conf as follows:
> 
Modem = /dev/ttyACM0
Baus = 230400
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Init3 = AT+CRM=1
Stupid Mode = 1
ISDN = 0
Modem Type = USB Modem
Phone = #777
Username = internet
Password = internet

And have also tried to configure Network Connection as explained in:

[https://answers.launchpad.net/ubuntu/+question/75832](https://answers.launchpad.net/ubuntu/+question/75832)

But am still unsuccessful to connect:(

Please help

---

### Post by prshah on 2009-09-26
> **hallenr said:**
> 
But am still unsuccessful to connect:(

These are digital phones, pulse dial is not supported. Use tone dial; ie, instead of  "ATM1L3DP#777" try ```
ATM1L3D[color=red]T[/color]#777
``` You can also drop the "M1" (Modem speaker on) and "L3" (Maximum modem speaker volume).

---

### Post by hallenr on 2009-09-26
Thanks, for the suggestion, but it was of no help:(

---

