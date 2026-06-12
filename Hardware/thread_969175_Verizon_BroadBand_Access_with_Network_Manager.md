---
title: "Verizon BroadBand Access with Network Manager"
date: 2008-11-03
forum: Hardware
---

### Post by CorporateGoth on 2008-11-03
Hi,

I have gotten my Verizon BroadbandAccess to work with Network Manager.  It does not show up as an option I can add however, but it auto-detected it.  I am not sure if this is because it previously worked (I had a ppp profile setup, and used to start it with 'pppd call ppp0').  Either way, it's working.

For those not familiar, you should only need to tell it to dial '#777', the password is '<phonenum>@vzw3g.com' and password is 'vzw'.  You only need CHAP authentication enabled.

This is all well and good, but there is one problem.  I am not sure what is requiring it, the Verizon network, or my BroadbandAccess Card (the Sierra Wireless, Inc. MC5720 built into a T60p laptop).  But one of them will fail the LCP echos.

This means these options must be passed to pppd: lcp-echo-failure 65535 lcp-echo-interval 65535

Unfortunately, Network Manager has no optiont to pass this, but I have figured it out.  For anyone else in this situation, you must edit the file /etc/NetworkManager/system-connections/<your connection name>

Find the lines for the above options (will be something like lcp-echo-failure=0 or something) and set their values to 65535.  Then your Verizon BroadbandAccess connection will stop disconnecting after being only connected for a minute or two, which mine constantly did.

Hopefully future Network Manager versions will have an 'advanced' dialogue or something that lets you adjust things like the timeout without resorting to file editing.

---

