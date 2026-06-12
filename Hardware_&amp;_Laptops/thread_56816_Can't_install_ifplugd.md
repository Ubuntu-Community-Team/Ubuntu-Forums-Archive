---
title: "Can't install ifplugd"
date: 2005-08-14
forum: Hardware &amp; Laptops
---

### Post by andlinux on 2005-08-14
If I want to install ifplugd I get a message that it is standing in the database but ubuntu can't install it.

I tried to install it with apt-get install and with synaptic.

How can I solve this problem ?

---

### Post by s_p_a_r_k_y on 2005-08-14
hmmm thats awfully weird.

```

 sudo apt-get install ifplugd
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libdaemon0
The following NEW packages will be installed:
  ifplugd libdaemon0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 59.4kB of archives.
After unpacking 328kB of additional disk space will be used.
Do you want to continue [Y/n]?

```

It seems to just work for me

---

### Post by andlinux on 2005-08-14
I installed it now but I have no idea why it worked ?

---

### Post by s_p_a_r_k_y on 2005-08-14
your computer is probably set on random mode...that happens to me sometimes

---

### Post by andlinux on 2005-08-15
[QUOTE=s_p_a_r_k_y]your computer is probably set on random mode...that happens to me sometimes[/QUOTE]
 :smile:

---

