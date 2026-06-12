---
title: "How to run a script when IP-address changes?"
date: 2008-09-07
forum: General Help
---

### Post by tnek on 2008-09-07
Hi,

I have a script to update a dynamic DNS service (not DDNS compatible, thus I must use my own custom script for updating) which I would like to run when the IP-adress of my (only) NIC eth0 changes. These changes will arrive through DHCP.

Is there any Upstart event I could connect my script through and have it run only when needed? This would be the best solution.

A less elegant solution would be to run the script once every hour as a cron job. But it would work.

In both of the solutions I would think that I create a new user account which has as its sole purpose to be the running this script from computer boot up? (I don't want to have to be logged in to run the script.)

All help is welcome! I would most of all like to get ideas on how to get this working using Upstart.

---

### Post by hyper_ch on 2008-09-07
dyndns.org and noip.com have clients in the repos that you can simply use to update entries.

---

### Post by tnek on 2008-09-07
[QUOTE=myself]not DDNS compatible, thus I must use my own custom script for updating[/quote]
This means I can not use their clients. I have to use my own script. My original question remains unsolved. :)

---

### Post by sdennie on 2008-09-07
Depending on how you want to do things, you can likely just drop your script into /etc/dhcp3/dhclient-exit-hooks.d/ or /etc/dhcp/dhclient-enter-hooks.d.  I'm not familiar with either but it sounds like what you are looking for.

---

### Post by tnek on 2008-10-06
If I drop my script into /etc/dhcp3/dhclient-exit-hooks.d/ or /etc/dhcp/dhclient-enter-hooks.d and it gets executed when my IP-address is updated. As which user account is the script run? So I get the file permissions right.

---

