---
title: "Password for root on vanilla installation"
date: 2008-12-01
forum: General Help
---

### Post by arell on 2008-12-01
I wanted to change the partitions on a spare disk and found I needed to sign on as 'root' to do it, but do not know the password for root.  Any ideas?

---

### Post by taurus on 2008-12-01
Use sudo/gksudo.  What exactly do you plan to do?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by aysiu on 2008-12-01
You don't need to sign in as root to do it. Install GParted and then go to System > Administration > GParted

If you don't know how to install software, go [here](http://www.psychocats.net/ubuntu/installingsoftware).

---

### Post by arell on 2008-12-03
I looked but could not find GParted; where is it located?  In any case, thanks for your help to this point.

---

### Post by Titan8990 on 2008-12-03
You should click on aysiu's article on installing software. You need to install gparted from the Synaptic Package Manager.

---

### Post by arell on 2008-12-03
Thanks for your reply.  I tried sudo/gksudo as password for root, I tried user sudo with password gksudo, and neither works.  Could you tell me what I am doing wrong?

---

### Post by Titan8990 on 2008-12-03
> **arell said:**
> Thanks for your reply.  I tried sudo/gksudo as password for root, I tried user sudo with password gksudo, and neither works.  Could you tell me what I am doing wrong?



You didn't read the article about sudo that was in post #2. That is what you did wrong.

---

### Post by the yawner on 2008-12-03
You'll need to install it first. See Aysiu's link for details.

> **aysiu said:**
> You don't need to sign in as root to do it. Install GParted and then go to System > Administration > GParted

If you don't know how to install software, go [here](http://www.psychocats.net/ubuntu/installingsoftware).

---

