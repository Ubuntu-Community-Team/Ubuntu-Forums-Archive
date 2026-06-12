---
title: "second ethernet device"
date: 2010-02-25
forum: Hardware
---

### Post by pavel989 on 2010-02-25
ey everyone,
i got a home server running. I want to make it the entry point to my LAN and internet. I installed a second Ethernet card and installed dhcp3. But i have never configured 2 ethernet devices, and im not sure how to set the second one (eth1 i presume) to take dhcp/dns options from the computer itself

anyone point me into the right direction?

---

### Post by booshire on 2010-02-25
> **pavel989 said:**
> ey everyone,
i got a home server running. I want to make it the entry point to my LAN and internet. I installed a second Ethernet card and installed dhcp3. But i have never configured 2 ethernet devices, and im not sure how to set the second one (eth1 i presume) to take dhcp/dns options from the computer itself

anyone point me into the right direction?

A NIC set to DHCP should broadcast to all to find the DHCP server. It should see at least the external address of the internal DHCP server. Maybe I am wrong.

---

### Post by pavel989 on 2010-02-25
> **booshire said:**
> A NIC set to DHCP should broadcast to all to find the DHCP server. It should see at least the external address of the internal DHCP server. Maybe I am wrong.

how would i go about broadcasting to all

---

