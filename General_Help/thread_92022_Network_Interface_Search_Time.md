---
title: "Network Interface Search Time??????"
date: 2005-11-18
forum: General Help
---

### Post by sfagundes on 2005-11-18
Is there a way to decrease the amount of time that ubuntu tries to bring up a network interface during the boot process.  On my laptop if I am in the field I dont always have a connection and it sits there for at least 20-30 seconds trying to auto-config my interfaces.

thanks!

---

### Post by Dr. Nick on 2005-11-18
if you know its not going to have a connection and you dont need one on that session hit ctrl+c and it will skip over it. You can bring the card up manually using "sudo ifup eth0" or similar once booted if needed.

Mine is the same way

---

### Post by kroiz on 2005-11-18
You can change the timeout in /etc/dhcp3/dhclient.conf

the default is 60 seconds but on my laptop I set it to 5 seconds.

---

