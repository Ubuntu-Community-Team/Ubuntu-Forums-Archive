---
title: "change welcom screen"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by herrbrand on 2008-12-25
hello

I have ubuntu server editie 8.04 LTS running on my server and i want to change the massage what ubuntu gives directley after i loged in.

where can i costomize this massage?

i mean this message:
```

Last login: Thu Dec 25 03:48:44 2008 from 192.168.2.2
Linux Server 2.6.24-19-server #1 SMP Wed Jun 18 15:18:00 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

```

Robbert

---

### Post by Partyboi2 on 2008-12-25
To change the MOTD (message of the day) you should be able to edit /etc/motd 
```
sudo nano /etc/motd
```

---

