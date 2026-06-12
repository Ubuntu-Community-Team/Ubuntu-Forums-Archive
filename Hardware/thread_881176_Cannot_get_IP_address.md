---
title: "Cannot get IP address"
date: 2008-08-05
forum: Hardware
---

### Post by DaemonLee on 2008-08-05
I have a; 

HP Pavillion 6700 CTO laptop

I am unable to get an IP address via DHCP, But, I was able to before I started to alter my firewall rules.

I locked myself out, on all ports using lokkit, and then decided to reinstall (new install, why not.) And now, it will not get an IP at all. 

Tested cable, good. Used another laptop, good. 


Help? :(


Edit: Network Manager is using the driver of forcedeth for ETH. Also, my ethernet numbers keep on changing, except for ETH3 (wired). 

Thanks.

---

### Post by neilneil2000 on 2008-08-05
I assume other devices on your network can get IPs via DHCP?

Have you tried allocating your laptop a static IP and pinging the default gateway.

Also it would be useful for you to post the output of this command:
```

sudo iptables -L

```

---

