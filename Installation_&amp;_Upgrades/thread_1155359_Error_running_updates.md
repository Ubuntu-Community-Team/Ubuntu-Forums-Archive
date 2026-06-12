---
title: "Error running updates"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by CoCoKnots on 2009-05-10
A couple of updates ago I received a couple of errors which I am not able to get beyond. Now whenever I try to install a standard Ubuntu update using Hardy 8.04 I first receive the first error message followed by the second by trying to install a partial update as recommended. This occurs with each attempt. I'm not certain, but it looks like what ever error is in the system is also effecting my being able to connect to the internet. Any Ideas. Thanks

---

### Post by taurus on 2009-05-10
Close down the update manager first.  Then, open a terminal and post the output of this command here.

```
sudo apt-get update
sudo apt-get dist-upgrade
```
Otherwise, post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by wpshooter on 2009-05-10
Have you tried switching to a different Ubuntu server ?

---

### Post by CoCoKnots on 2009-05-10
> **taurus said:**
> Close down the update manager first.  Then, open a terminal and post the output of this command here.

```
sudo apt-get update
sudo apt-get dist-upgrade
```
Otherwise, post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

Thanks Taurus, I ran the terminal commands as suggested. It looks like that took care of the problem. No Error Message when I went back into the Update Manager. Thanks again.:guitar:

---

