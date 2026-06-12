---
title: "dnsmasq Confusion"
date: 2008-09-23
forum: General Help
---

### Post by klausner on 2008-09-23
I have dnsmasq installed to get around Speakeasy's miserable DNS responses. But the prepend statement isn't working properly. If I cat resolv.conf, I get:
> nameserver 127.0.0.1
nameserver 4.2.2.2
nameserver 216.254.95.2

The 127.0.0.1 is (I assume) coming from the line > listen-address=127.0.0.1
in the file /etc/dnsmasq.conf. The latter two addresses are coming from my own router. 

The file /etc/dhcp3/dhclient.conf is set to:
> prepend domain-name-servers 127.0.0.1,4.2.2.2,216.254.95.2,66.93.87.2,64.81.111.2,4.2.2.5,55.92.192.2,4.2.2.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;


(which is a mix of Speakeasy and other DNS), but none of this shows up in resolv.conf, either after a reboot, or after a > /etc/init.d/dnsmasq restart.

Clearly I'm doing something wrong here, but I don't know what.

---

### Post by lil_elvis2000 on 2008-09-23
have you tried removing _domain-name-servers _from your dhclient.conf file?

You need to do a networking restart I think after changing this file.

---

### Post by klausner on 2008-10-01
> **lil_elvis2000 said:**
> have you tried removing _domain-name-servers _from your dhclient.conf file?

You need to do a networking restart I think after changing this file.

Logically, that should break everything. Tried it though, and there was absolutely no effect.

---

