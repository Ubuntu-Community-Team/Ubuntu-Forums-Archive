---
title: "Daisy chaining displayport for dual monitors with Ubuntu 17.10"
date: 2017-12-21
forum: Hardware
---

### Post by sawfish2 on 2017-12-21
Just wanted to share a small success, because I had trouble finding information on using daisy chained displayport for dual monitors with Linux. Initially I had some trouble to get it working, but after installing Ubuntu 17.10 and using the correct setting of the monitors (enable DP1.2 in the monitor connected to the motherboard and disabling DP1.2 in the other) it runs to my full satisfaction.

 I have a ASUS Z170-A motherboard and use the on board graphic chip (Intel) to drive two Dell U2515H at full resolution (2560 x 1440). I don't use it for gaming, but CAD programs runs without any problems. I am surprised how smoothly this graphic chip run the displays, and after spending a fair amount on monitors, it is nice to avoid extra costs for a dedicated graphic cards to drive them. Eventually I properly will buy a graphic card to speed up large CAD models.

                        Kind regards
 Sawfish2

---

### Post by svast on 2018-01-02
Thank you for sharing.
Can you write if you are using vanilla kernel provided with ubuntu 17.10, or custom version? anyway, Which version of linux kernel are you using to make it happen?

best regards,
Stephane

---

### Post by sawfish2 on 2018-01-03
> **svast said:**
> 
Which version of linux kernel are you using to make it happen?


As the download from the official site was closed, I used the ISO image from another place. Unfortunately I don't remember which.
The uname -r command gives me 4.13.0-21-generic.

Kind regards
Sawfish2

---

