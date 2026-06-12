---
title: "Remote control of hibernate- or hibernate for unprivileged users?"
date: 2007-08-02
forum: Hardware &amp; Laptops
---

### Post by NigO on 2007-08-02
I would like to be able to hibernate a machine on my network under direct control of another machine on the network, with no human interaction.  I can successfully hibernate manually by using ssh to connect, then ```
sudo /etc/acpi.hibernate.sh
``` to start the hibernate.

I have set up ssh keys so I can connect automatically to be machine to be hibernated, so now on the controlling machine, I would like to do something like ```
ssh 192.168.101.2 /etc/acpi/hibernate.sh
```

However, that doesn't work as various parts of hibernate.sh need root privileges.  Yet any user can click the 'hibernate' option on the logout screen, is there a command line equivalent?

Nigel

---

