---
title: "aurora install fail"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by masterchief1995 on 2009-03-09
hi, I was wondering if anyone can help me fix this error message I got while using the **./configure**command while installing aurora from source and this is what I got
[CODE]debian:/home/user/Desktop/aurora-1.5# ./configure

checking for a BSD-compatible install... /usr/bin/install -c

checking whether build environment is sane... yes

checking for a thread-safe mkdir -p... /bin/mkdir -p

checking for gawk... no

checking for mawk... mawk

checking whether make sets $(MAKE)... no

checking whether to enable maintainer-specific portions of Makefiles... no

checking for gcc... no

checking for cc... no

checking for cl.exe... no

configure: error: no acceptable C compiler found in $PATH

See `config.log' for more details.
/CODE]
any help is appreciated
P.S. I have a fairly old laptop running debian 5.0 without a direct connection to the internet, but I do have a desktop with a connection so I can't use synaptic or aptitude.

---

### Post by taurus on 2009-03-09
You need to install gcc compiler first before you can build anything from source.

```
sudo apt-get update
sudo apt-get install build-essential
```

And if you don't have a direct connection to the net, then insert Ubuntu install CD into the drive and install build-essential package from the CD.

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

Now, run the **./configure** again.

---

### Post by masterchief1995 on 2009-03-12
thanks, I will definitely try that.:D

---

