---
title: "OpenVPN won't start"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by mocka on 2009-09-22
I have now tried to install openvpn by following command:

```
sudo apt-get install openvpn
```

The only output that comes on screen when I try to start the openvpn daemon is:

```
mocka@HubuntuServer:~$ sudo /etc/init.d/openvpn start
 * Starting virtual private network daemon(s)...     *   Autostarting VPN 'server'   [fail]
```

What am I doing wrong? Note: I use Ubuntu Server x64

---

### Post by Lieter on 2009-09-22
You should probebly configure it before you can use it.

have a look at [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN) and [http://www.thebakershome.net/openvpn_tutorial](http://www.thebakershome.net/openvpn_tutorial)

---

### Post by mocka on 2009-09-22
I already tried the first tutorial you provided, but it did not make any difference.

EDIT: I will try the second one, it seems more elaborated.

UPDATE: The second tutorial did not work either, though I at least got an error message. Therefore it seems like my previous problem was that OpenVPN was not configured.

---

### Post by nur fadilah on 2010-05-26
yup, i'm also have same problem like mocka.
it have took almost 2 week for me to configure the problems but still didnt find any solution..

please help me, i'm doing intern right now for 2 months and i didnt have much time.:(

---

### Post by dirtrider1 on 2011-08-20
I'm having the same issue

---

