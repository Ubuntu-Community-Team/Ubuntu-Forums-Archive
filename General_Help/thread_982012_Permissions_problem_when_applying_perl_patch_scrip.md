---
title: "Permissions problem when applying perl patch script to dc++"
date: 2008-11-14
forum: General Help
---

### Post by chezzo on 2008-11-14
Hi, I'm trying to get my University's DC++ network working on Ubuntu 8.10, by following the instructions here - [http://camdcwebsite.ath.cx/](http://camdcwebsite.ath.cx/)
Specifically
> The following steps have been known to get a working linux client on debian and ubuntu. Modify as needed for your own distro.

sudo apt-get update
sudo apt-get install linuxdcpp
sudo cp /usr/bin/linuxdcpp /usr/bin/linuxdcpp.bak
sudo wget [http://camdcwebsite.ath.cx/dcpatch.txt](http://camdcwebsite.ath.cx/dcpatch.txt)
sudo perl dcpatch.txt < /usr/bin/linuxdcpp.bak > /usr/bin/linuxdcpp
# and to launch it:
/usr/bin/linuxdcpp
However, when I get to the perl command, applying the patch, terminal simply gives me the message "bash: /usr/bin/linuxdcpp: Permission denied". What am I doing wrong?
Thanks!

---

### Post by taurus on 2008-11-14
Maybe try something like

```
sudo perl dcpatch.txt < /usr/bin/linuxdcpp.bak > **sudo** /usr/bin/linuxdcpp
```

---

### Post by chezzo on 2008-11-14
sorry, doesn't work... it creates a 2mb file in my home directory called "sudo"

---

### Post by chezzo on 2008-11-14
bump

---

### Post by chezzo on 2008-11-14
bump

---

### Post by chezzo on 2008-11-17
bump

---

### Post by kbuel on 2008-11-17
you could run the command as root I guess:

running:

sudo su

switches you to root.


or you could break it up into multiple steps:
perl dcpatch.txt < /usr/bin/linuxdcpp.bak > /tmp/linuxdcpp
sudo mv /tmp/linuxdcpp /usr/bin/linuxdcpp

---

### Post by chezzo on 2008-11-19
hmm still doesn't seem to be working

or rather, i think it is working, but the patch doesn't seem to be doing anything... maybe there's something wrong with it

the windows version just about works under wine, so i can use that instead

---

