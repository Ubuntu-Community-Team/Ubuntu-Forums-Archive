---
title: "little networking help if you please ;) (pptp,nat)"
date: 2012-06-21
forum: Hardware
---

### Post by Shadowstripe on 2012-06-21
Hi

I followed this guide 

[http://www.larmeir.com/2010/03/setting-up-a-pptp-vpn-server-on-debian-and-ubuntu/](http://www.larmeir.com/2010/03/setting-up-a-pptp-vpn-server-on-debian-and-ubuntu/)

I completed all the steps only  changing the user details and the internal and external ip addresses (I tried both an unused ip on my routers current range and a different local network ip range)

so far the pptp server works like a charm I am able to connect in from an external address and ping the device as if it were on the network under both ip addresses but I just can't get external internet access from the connected device.

I guess the guide is a little old but is there anything that has changed or any suggestions on what I can do to get internet access working ?

(I also installed the optional bind9 and tried going to a website direct via ip address with no luck)

Thank you

---

### Post by Shadowstripe on 2012-06-22
after several hours I figured out its something to do with the vpn connecting using that machine as a gateway and not the router or something anyway given up on it and given machine back he will have to be happy with just ubuntu installed on it

---

