---
title: "Wireless issues after return from hibernate"
date: 2008-04-30
forum: Hardware
---

### Post by poorgeek on 2008-04-30
I'm having an interesting issue with my new Heron install where the wireless on my Dell E1505 won't connect to my secure (WPA Personal) access point after returning from hibernate. I am able to connect to other non-secure networks fine following a hibernate and if I reboot I am able to connect to my secure network again just fine. Occasionally the network manager will register that I am connected but for some reason I'm not getting an IP address, gateway, etc... from DHCP.

Its all very weird.

My guess is that something isn't getting cleaned up along the way but I have no idea what that might be or really where to start looking. Does anyone know if there is a way to restart wireless after returning from hibernate, or even better, is there a fix for this issue?

Thanks,

- Justin

---

### Post by VeN0mizer on 2008-04-30
I have a similar problem with my E1505, after I resume from suspend, Network Manager keeps nagging me for my WPA password, which _should_ be saved. I put in in, and it only gets one green light, and simply reprompts me for my credentials...I have to reboot to get wireless back..I'm thinking of going back to WICD :/

---

### Post by poorgeek on 2008-04-30
A Google search post coffee yielded an answer:
[https://bugs.launchpad.net/ubuntu/+bug/69426](https://bugs.launchpad.net/ubuntu/+bug/69426)

Turns out I just need to add "networking" to the STOP_SERVICES item in /etc/default/acpi-support.

A nice tidy fix.

---

