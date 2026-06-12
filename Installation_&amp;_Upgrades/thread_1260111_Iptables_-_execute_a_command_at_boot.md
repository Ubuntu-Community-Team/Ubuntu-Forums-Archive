---
title: "Iptables - execute a command at boot"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by herrfledermaus on 2009-09-07
hi there,

I installed ubuntu as a gateway/server and it works fine: finally I have my gateway and also a java enabled LAMP jboss and such thing at home to study java. Since it also acts as a dhcp server on the local lan, I have only one question left:

after a reboot, I have to go into a terminal and execute the following command:

iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE

Only after this command the clients are able to access the internet. Can someone tell me how I can permanently add this command at server startup, by using webmin or a terminal window?

thanks for the help,

fledermaus

:guitar:

---

### Post by herrfledermaus on 2009-09-07
FYI: gnome is also running on that machine...

---

### Post by BadBoy4Live on 2009-09-07
I would suggest you to create a new file in the directory /etc/init.d/
In this file you would put the command that you want to run.

Create the file and insert the command that you want to run in the file

```
sudo gedit /etc/init.d/example
```Set proper permissions to execute

```
 sudo chmod +x /etc/init.d/example
```Then add it to startup

```
 sudo update-rc.d example defaults
```

---

