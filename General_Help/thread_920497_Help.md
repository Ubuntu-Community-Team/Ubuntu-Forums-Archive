---
title: "Help???"
date: 2008-09-15
forum: General Help
---

### Post by jcferrer on 2008-09-15
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by tuxxy on 2008-09-15
Try opening a terminal and running this command to correct the issue
, this usually due to you interrupting an update

```
sudo dpkg --configure -a
```

---

### Post by jcferrer on 2008-09-15
sudo: unable to resolve host splinter-desktop....sir this is the message

---

### Post by jcferrer on 2008-09-15
You have 1 broken package on your system!

Use the "Broken" filter to locate it.

---

### Post by tuxxy on 2008-09-15
Open synaptic package manager, and navigate to **Edit > Fix broken pkg**

---

### Post by iaculallad on 2008-09-15
> **jcferrer said:**
> sudo: unable to resolve host splinter-desktop....sir this is the message

Post whatever displays when you issue the command below on your terminal:

```
cat /etc/hosts
```

Do include your terminal prompt: I.E:

> **[COLOR="DarkRed"]ian@[COLOR="Blue"][B]gutsy-gibbon**[/COLOR]:~$ cat /etc/hosts[/COLOR][/B]
127.0.0.1 localhost
127.0.1.1 [COLOR="Blue"]**gutsy-gibbon**[/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


EDIT:

Be sure that whatever hostname outputs in the command **cat /etc/hosts** should equal that of your terminal prompt.

From the error message that displayed when you typed **sudo dpkg --configure -a**, I can see that your /etc/hosts file contains **splinter-desktop** name. Try changing:

> 127.0.1.1 splinter-desktop

to equal that of your prompt (see the colored blue texts above).

---

