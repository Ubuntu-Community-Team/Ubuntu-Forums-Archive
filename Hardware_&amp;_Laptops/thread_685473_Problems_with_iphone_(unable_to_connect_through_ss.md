---
title: "Problems with iphone (unable to connect through ssh)"
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by olavjunior on 2008-02-02
I have followed the guide [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone). 

But it stopped after step two. I tried manual ssh by ssh 10.0.0.3 -l root, -nothing..
I tried nmap 10.0.0.3 giving me ```
Starting Nmap 4.20 ( http://insecure.org ) at 2008-02-02 15:12 CET
Note: Host seems down. If it is really up, but blocking our ping probes, try -P0
Nmap finished: 1 IP address (0 hosts up) scanned in 4.003 seconds

```

Any ideas?

Also, trying iphone-mount, gives me an error: re```
ad: Connection reset by peer
``` after a few minutes


EDIT: I changed the wifi to dchp, and then it worked :)

---

