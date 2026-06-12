---
title: "Can't access LAN devices (ping, ssh, ftp, telnet, nada)"
date: 2008-11-03
forum: General Help
---

### Post by rkrizan on 2008-11-03
I can't access any of my network devices. I can ping out, to google.com, and whatever else, but nothing within my LAN. I can ping my Ubuntu machines from a Windows machine without a problem. But I can't ping ANYTHING on my LAN from Ubuntu (8.10)

Any suggestions?

Thanks

---

### Post by Portmanteaufu on 2008-11-03
This is probably a silly question, but are you using a hostname or the ip address to ping the other computers on your network?

e.g. If you had a computer on your network named "superman" with the ip address 192.168.1.101, are you doing:
```
ping superman
```
or
```
ping 192.168.1.1
```
?

I ask because Windows uses Active Directory to keep track of which computers have which host names, while Linux uses a file called /etc/hosts to figure out the nicknames that you hand it.

If you're using a Windows box it will have an IP address to try. If you're using a Linux box and superman isn't in /etc/hosts then it will probably not be able to resolve the destination.

Or maybe it's something else altogether. Could you post the commands you're trying and their output?

---

