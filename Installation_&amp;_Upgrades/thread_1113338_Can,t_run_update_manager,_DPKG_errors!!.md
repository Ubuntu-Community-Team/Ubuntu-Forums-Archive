---
title: "Can,t run update manager, DPKG errors!!"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by Julian David Pitt on 2009-04-01
When I try an install or run update manager from the terminal I get the following error:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

When I run this command I then get another error:

```
julian@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for julian:
dpkg: parse error, in file `/var/lib/dpkg/status' near line 22714 package `libgail18':
 field name `
julian@ubuntu:~$
```

Can anyone please offer some help on these errors, thank you in advance.

---

### Post by gjoellee on 2009-04-01
Have you tried to reboot? Sometimes that will solve apt problems...

---

### Post by Julian David Pitt on 2009-04-02
Thanks for responding gjoellee. I don't believe a restart will solve things as the issue has been there since I had to kill the system after having some dodgy ram mess me about. It has been rebooted quite a few times since and each time I try to install updates I get this, can you shed any further light on what the specifics of the error mean?

---

### Post by Partyboi2 on 2009-04-02
Open a terminal and try
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.broke
```
then 
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```
```
sudo dpkg --configure -a
```

---

### Post by Julian David Pitt on 2009-04-02
That worked a treat so thank you very much indeed.

---

