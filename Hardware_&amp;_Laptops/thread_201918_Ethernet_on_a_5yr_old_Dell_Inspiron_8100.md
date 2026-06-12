---
title: "Ethernet on a 5yr old Dell Inspiron 8100"
date: 2006-06-22
forum: Hardware &amp; Laptops
---

### Post by wreckingcru on 2006-06-22
Hey all,
Trying to install BB 5.10 on a Dell Inspiron 8100 "BRICK" with 128mb RAM. Everything looks fine except for internet.

eth0 is being detected fine. I can even log on to my Vonage Router's webpage (15.1) and navigate it.

But when I try google.com or any other website, it times out. I'm using onboard ethernet and not wireless or anything external. 
I've tried DHCP and static IP. tried 'ifup eth0' and get 'eth0 is already configured'.

The only error message of any relevance is:
$ifconfig /all
/all: error fetching interface information: Device not found.


Any suggestions what I can do? I would really like to keep Ubuntu on my parents' computer to improve speed and better virus and spyware protection (even if it's superficial).

Thanks!

---

### Post by jrattner on 2006-06-22
Take a look at your /etc/resolve.conf

This file should have a list of your nameservers.  I'm assuming (and I could be wrong) that this is why your having trouble resolving websites.  Add your name servers here and you should be good to go!

---

### Post by wreckingcru on 2006-06-22
[QUOTE=jrattner]Take a look at your /etc/resolve.conf

This file should have a list of your nameservers.  I'm assuming (and I could be wrong) that this is why your having trouble resolving websites.  Add your name servers here and you should be good to go![/QUOTE]


How would I find my nameservers? For XP, all I did was bring in my own laptop and plugged in the ethernet jack and I was online (DHCP was setup)...Can I determine the nameservers from this XP box to setup on the Dell laptop?

---

### Post by jrattner on 2006-06-23
In XP, click on the network icon on the toolbar (the picture of the litle computer) and go to status-->Support and then details.

Under the details screen you will see an entry called DNS servers.  Write down that IP address and save in /etc/resolve.conf

User the following format

nameserver IP address


For example: (/etc/resolve.conf)
nameserver 72.68.216.251

---

