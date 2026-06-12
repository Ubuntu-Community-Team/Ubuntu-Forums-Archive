---
title: "sudoers PB changing rights"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by steveJames76 on 2009-03-17
Hi,

I made a mistake, by changing the right of /etc/sudoers ( iI put 777 )
Now, I cannot shutdown hte PC by command line :  sudo /sbin/shutdown -h now )

If I try to come back with previous config on sudoers , I have :

toto@toto-ubuntu:~$ sudo chmod 0440 /etc/sudoers
sudo: /etc/sudoers is mode 0777, should be 0440


Any idea what could be the problem ?

thanks

---

### Post by iaculallad on 2009-03-17
Try:

```
sudo chown root:root /etc/sudoers
sudo chmod 0220 /etc/sudoers
```

And

```
sudo shutdown -h now
```

---

