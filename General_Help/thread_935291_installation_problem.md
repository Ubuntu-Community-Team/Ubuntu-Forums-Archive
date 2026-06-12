---
title: "installation problem"
date: 2008-10-01
forum: General Help
---

### Post by Joseph82 on 2008-10-01
Hi

I have downloaded a php-editor from net and when I typed the configure as instructed in the installation file, got the following:


[root@localhost joseph]# cd ./Download/anjuta-2.23.91
[root@localhost anjuta-2.23.91]# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.


Please help me to fix this 

Thank You,
An. Joseph

---

### Post by MunkyJunky on 2008-10-01
I know this is a little silly to say, presumably you have no C compiler installed. Try reading the config.log file, may point you in the direction of a solution.

---

### Post by Yellow Pasque on 2008-10-01
anjuta is available in the repos and I would recommend using that version. If you still want to build your version from source, use this to get all the necessary dependencies:
```
sudo apt-get build-dep anjuta
```

BTW, the immediate error is that you don't have a compiler installed. Make sure you at least:
```
sudo apt-get install build-essential
```

---

### Post by Joseph82 on 2008-10-01
> **Temüjin said:**
> 
```
sudo apt-get build-dep anjuta
```

```
sudo apt-get install build-essential
```


I have tried that and got the following:


[root@localhost joseph]# sudo apt-get install build-essential
sudo: apt-get: command not found
[root@localhost joseph]# sudo apt-get build-dep anjuta
sudo: apt-get: command not found

---

### Post by Yellow Pasque on 2008-10-01
If you're root, don't use sudo:
```
apt-get build-dep anjuta
apt-get install build-essential
```

---

