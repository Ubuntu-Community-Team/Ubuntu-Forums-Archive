---
title: "apt-get broken"
date: 2008-08-25
forum: General Help
---

### Post by weweboom on 2008-08-25
when I open a terminal and use sudo apt-get whatever, it responds with unable to resolve host Duncan, What is wrong?

---

### Post by -Zeus- on 2008-08-25
> **weweboom said:**
> when I open a terminal and use sudo apt-get whatever, it responds with unable to resolve host Duncan, What is wrong?

Please paste the EXACT output of ```
sudo apt-get update
```

---

### Post by sisco311 on 2008-08-25
post the output of:
```
cat /etc/hosts
```

---

### Post by weweboom on 2008-08-25
sudo apt-get update gave me
can't resolve host Duncan 

cat /etc/hosts gave me 
# The following lines are desirable for IPv6 capable hosts
# (added automatically by netbase upgrade)

::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by -Zeus- on 2008-08-25
> **weweboom said:**
> sudo apt-get update gave me
can't resolve host Duncan 

cat /etc/hosts gave me 
# The following lines are desirable for IPv6 capable hosts
# (added automatically by netbase upgrade)

::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

SO it looked EXACTLY like this?
```
blah@blah:~$ sudo apt-get update
can't resolve host Duncan
```

are you sure you're connected to the internet?

---

### Post by weweboom on 2008-08-25
yes, I can browse the internet

---

### Post by redilyn on 2008-08-25
Did you make any changes to your host names?

you should have:

127.0.1.1 Duncan

in /etc/hosts

It is likely the sudo command is not working for you now, you may have to boot into recovery mode to make that change.

Change /etc/hosts to:

127.0.1.1 Duncan

# The following lines are desirable for IPv6 capable hosts
# (added automatically by netbase upgrade)

::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by drs305 on 2008-08-25
It appears your computer's id has been dropped by hosts. Edit the file and add the lines below.

```

sudo cp /etc/hosts/ /etc/hosts.old
gksu gedit /etc/hosts
```

Add the following lines:
```

127.0.0.1 localhost
127.0.1.1 *yourcomputername*

```

---

### Post by sisco311 on 2008-08-25
edit the file:
```
gksu gedit /etc/hosts
```

and add the following lines:
> [B]127.0.0.1    localhost
127.0.1.1    Duncan
[/B]
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by weweboom on 2008-08-25
I added those lines but I'm still seeing unable to resolve host Duncan

---

### Post by sisco311 on 2008-08-25
Try to log out and log back in or reboot.

---

