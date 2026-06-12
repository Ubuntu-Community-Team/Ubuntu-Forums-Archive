---
title: "Woke up this mourning and can't connect to the Internet."
date: 2008-08-24
forum: General Help
---

### Post by u-slayer on 2008-08-24
Computer was working fine yesterday, but today I can't connect to the Internet. When I boot into windows, the Internet works just fine so I know that it's not a hardware issue. 

What's even stranger is that the network icon shows me to be connected, however when I click on "connection information" it tells me that I am connected at 1000Mb/s and my IP address is 0.0.0.0:confused:

---

### Post by mssever on 2008-08-24
> **u-slayer said:**
> Computer was working fine yesterday, but today I can't connect to the Internet. When I boot into windows, the Internet works just fine so I know that it's not a hardware issue. 

What's even stranger is that the network icon shows me to be connected, however when I click on "connection information" it tells me that I am connected at 1000Mb/s and my IP address is 0.0.0.0:confused:
Wireless or wired?

Does the following solve anything? ```
sudo /etc/init.d/networking restart
```If not, please post the full terminal output.

---

### Post by Iowan on 2008-08-24
If networking restart doesn't work, posting your **/etc/network/interfaces** file might shed some light.

---

### Post by u-slayer on 2008-08-24
I was going to try your idea so I booted up the computer and suddenly it works. (Mind you, that I have tried rebooting several times already)


***shrugs***

---

### Post by mssever on 2008-08-25
> **u-slayer said:**
> I was going to try your idea so I booted up the computer and suddenly it works. (Mind you, that I have tried rebooting several times already)


***shrugs***
Glad it works now. Don't you love problems that fix themselves? :)

---

### Post by u-slayer on 2008-08-25
> **mssever said:**
> Glad it works now. Don't you love problems that fix themselves? :)

No. I like problems that are repeatable given well-defined circumstances.

---

### Post by kenny001 on 2008-08-25
My computer some times is not connecting to the internet directly. It is showing some problems regarding the IP address. what should i do?
====================================================================
kenny

[North Dakota Drug Addiction](http://www.drugaddiction.net/north-dakota)

---

