---
title: "Setting up an Internal Web Server?"
date: 2008-11-03
forum: General Help
---

### Post by bigfredlab on 2008-11-03
I have a small home network that can access the internet through a linksys router/firewall (via cable modem).  Yesterday, I installed the desktop version of Ubuntu (Hardy).

I would like to know if it is possible to set up a web server on it for development purposes.  I don't want it be visible from the outside, just inside the network.

Is this possible?
Is there a good tutorial on how to do this?

Any help would be appreciated.

---

### Post by rhodry on 2008-11-03
Here you go:

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_for_local_web_development](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_for_local_web_development)

Cheers,
Rhodry

---

### Post by bigfredlab on 2008-11-03
Thanks Rhodry.

Will I be able to "see" the LAMP server from other machines (incl. windows machines) on my network?

---

### Post by Monotoko on 2008-11-03
If you put that machines internal IP address in, whilst LAMP is running, you should be able to :)

And if you are behind a router, and havent port-forwarded port80, people should not be able to gain access from the outside, only inside the network via internal IP (192.168.x.x)

---

### Post by bigfredlab on 2008-11-03
for example:


[http://192.100.50.50/index.html](http://192.100.50.50/index.html)

Is that correct?

No port forwarding.

---

### Post by Monotoko on 2008-11-03
If thats the computer thats running the websites internal IP, then yes
(i cant tell because im not in your network, only people inside the network can access stuff through internal IP's)

and if theres no port-forwarding it will mean its impossible to get into from the outside anyways (well...not impossible, but unlikley anyone would go to such lengths)

---

### Post by bigfredlab on 2008-11-03
No not the actual IP, just a reasonable facsimile.

Thanks for the help!

---

### Post by Iowan on 2008-11-03
[Here]("https://help.ubuntu.com/community/ApacheMySQLPHP") is another good LAMP How-To.

---

