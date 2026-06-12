---
title: "segmentation faulty tree"
date: 2008-10-03
forum: General Help
---

### Post by kktaus on 2008-10-03
Hello,

Can you recommend a fix for this problem?

~$ sudo apt-get install python-dev
sudo: unable to resolve host kath-laptop
Reading package lists... Done
Segmentation faulty tree... 50%

---

### Post by Ryadt on 2008-10-03
Post the output of ```
cat /etc/hosts
```

---

### Post by kktaus on 2008-10-03
127.0.0.1 localhost
127.0.1.1 kkthompson.TSL

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by Ryadt on 2008-10-03
Do```
sudo gedit /etc/hosts
```
Replace kkthompson.TSL by the output of```
lshw | head -1
```

---

### Post by kktaus on 2008-10-03
Thank you.
This solves the problem of host name resolution, but I still get an error message:
 sudo apt-get install python-dev
 
Reading package lists... Done
Segmentation faulty tree... 50%

---

### Post by Ryadt on 2008-10-03
Make sure that you've got universe and multiverse enabled in the repos.
Then try```
sudo apt-get update
```
Retry to install after that.

---

### Post by kktaus on 2008-10-03
Works now.

Thanks ever so much.

---

### Post by Ryadt on 2008-10-03
Great..;)
Please mark the thread as solved.

---

