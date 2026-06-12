---
title: "Cable Modem Help"
date: 2005-03-12
forum: Hardware &amp; Laptops
---

### Post by sethosayher on 2005-03-12
Now, I just installed Ubuntu yesterday. For some reason, using programs like Mozilla Firefox and Gaim, I can't connect or go online, and it appears that I can't access the internet. But when I go into the root terminal and enter commands like "apt-get update", it appears to connect to the servers with no problem...(I also downloaded software from the internet during the second stage of the install with no problem). One more thing, when I use the Live CD, Firefox, gaim, and the etc, connect with ease and I can surf at a whim. Is this a cable modem problem? A settings Problem?

I am using a **USB** , **Motorola Surfboard Sb4100 Cable Modem **.

---

### Post by sethosayher on 2005-03-12
A gentle BUMP >.>

---

### Post by sethosayher on 2005-03-13
Another Gentle BUMP. <_<

---

### Post by sethosayher on 2005-03-14
bump

---

### Post by alastair on 2005-03-14
I've no experience with cable modems but, since you have connected at some points, it's probably just a network config issue.

How do you access the cable modem? Ethernet?

ifconfig -a

route -n

cat /etc/resolv.conf

Some idea of how things are connected - modem <--> PC, and IP addresses.

---

### Post by sethosayher on 2005-03-15
[QUOTE=alastair]I've no experience with cable modems but, since you have connected at some points, it's probably just a network config issue.

How do you access the cable modem? Ethernet?

ifconfig -a

route -n

cat /etc/resolv.conf

Some idea of how things are connected - modem <--> PC, and IP addresses.[/QUOTE]

Its connected via USB. Do I enter those commands in the root terminal?

---

### Post by alastair on 2005-03-15
Yes - enter in a terminal (no need to be root). They are reporting only - no danger.

However, to check the log file you will need to "sudo" (or be root) - it is worth looking at :

/var/log/syslog

and seeing if you can see any USB/modem/network related lines - make sure no warnings or errors reported. Just in case. e.g.

sudo gedit /var/log/syslog

---

