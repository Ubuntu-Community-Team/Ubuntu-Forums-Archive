---
title: "CUPS server not working?"
date: 2008-09-05
forum: General Help
---

### Post by methodtwo on 2008-09-05
Hi there i'm tring to set ubuntu 7.10 up to act as a print server for my small network.The boxes(gentoo and ubuntu) are connected together using a router.I have opened up port 631(tcp and udp) on the router for the ubuntu server.Here are the relevant sections from /etc/cups/cupsd.conf:
```

<Location />
Order allow, deny
Allow localhost
Allow 192.168.2.102 (gentoo box)
</Location>
Listen *:631
Listen 192.168.2.102

```
and here are the relevant bits on the client side:
from /etc/cups/client.conf:
```
ServerNmae ubuntu

```
and from /etc/xinetd.d/cups-lpd
```
disable = no


```
However when i do:
```
lpr -H ubuntu:631 ./file.pdf

```
i get:
```
lpr: Error - scheduler not responding!
```
Any help would be great.Thankx in advance

---

### Post by Zurd on 2008-09-06
Typo, ServerName, not ServerNmae from client.conf

---

