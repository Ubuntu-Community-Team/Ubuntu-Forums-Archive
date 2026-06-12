---
title: "error main.cf"
date: 2008-08-27
forum: General Help
---

### Post by Low_E on 2008-08-27
When trying to edit conf-files a get a strange error-message suddenly:
> ludodg@olvbeta:~$ sudo gedit /etc/dhcp3/dhcpd.conf 
sudo: unable to resolve host olvbeta
sendmail: fatal: open /etc/postfix/main.cf: No such file or directory

Alldough, I am still able to log the "sudo-password" and edit the conf-file.



[edit]
It seems the /etc/postfix/main.cfg -file is suddenly missing.
Can someone tell me where this comes from, .. how I can repair this?

Thx

Ludo

---

### Post by Low_E on 2008-08-28
anyone pls

---

### Post by Ryadt on 2008-08-28
Can you post the output of ```
cat /etc/hosts
```

---

### Post by Low_E on 2008-08-28
here it is:

```
127.0.0.1 localhost
192.168.1.254 olvbeta.secundair olvbeta.secundair

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by Ryadt on 2008-08-28
> **Low_E said:**
> here it is:

```
127.0.0.1 localhost
192.168.1.254 olvbeta.secundair olvbeta.secundair

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

ok. Change it to this```
127.0.0.1 localhost
192.168.1.254 **olvbeta.secundair**

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by Low_E on 2008-08-28
Could you also explain me briefly what the error is?
How an error in hostst affects the fact that another file is missing?

thx



I did make the change, still get error-messages:
```
ludodg@olvbeta:~$ sudo gedit /etc/hosts
sudo: unable to resolve host olvbeta
sendmail: fatal: open /etc/postfix/main.cf: No such file or directory
ludodg@olvbeta:~$ 

```

maybe I should restart some process or service?

---

### Post by Ryadt on 2008-08-28
Firstly did it solve the problem?

---

### Post by Low_E on 2008-08-28
nope, I just even restarted the server and the same error-messages appear.

---

### Post by Ryadt on 2008-08-28
> **Low_E said:**
> nope, I just even restarted the server and the same error-messages appear.

Try```
gksudo gedit /etc/hosts
```

then```
127.0.0.1 localhost
192.168.1.254 **olvbeta**

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by Low_E on 2008-08-28
thx that fixed it.

So I guess the OS was looking for a certain file (that never existed), due to an error in this hosts-conf-file?

---

