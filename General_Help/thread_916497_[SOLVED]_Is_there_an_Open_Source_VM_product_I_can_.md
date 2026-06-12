---
title: "[SOLVED] Is there an Open Source VM product I can use in Ubuntu?"
date: 2008-09-11
forum: General Help
---

### Post by splicer707 on 2008-09-11
I would really like to run a Windows VM under Ubuntu.
But I'm a newb. Can someone help me? :KS

---

### Post by OutOfReach on 2008-09-11
How about [VirtualBox]("http://www.virtualbox.org/"), it's available in the repositories, just search 'virtualbox' in Synaptic.

---

### Post by jerome1232 on 2008-09-11
Virtual Box OSE (Open Source Edition)

```
sudo apt-get install virtualbox-ose
```

---

### Post by splicer707 on 2008-09-11
=D> Thankyou friends!

:KS :KS

---

### Post by p_quarles on 2008-09-11
QEMU is another open source virtualization application worth considering.

---

### Post by splicer707 on 2008-09-11
Help :confused: I must have done something wrong. Keep on getting this error...

---

### Post by p_quarles on 2008-09-11
> **splicer707 said:**
> Help :confused: I must have done something wrong. Keep on getting this error...
Run:
```
sudo apt-get install virtualbox-ose-modules-`uname -r`
```
You will also need to run:
```
sudo adduser $whoami vboxusers
```
and then restart your login session.

---

### Post by splicer707 on 2008-09-11
> **p_quarles said:**
> Run:
```
sudo apt-get install virtualbox-ose-modules-`uname -r`
```
You will also need to run:
```
sudo adduser $whoami vboxusers
```
and then restart your login session.

:KS Thankyou! All done. Working great now.

---

