---
title: "Upgrade help"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by JONATHAN AINOO on 2009-04-22
How can i upgrade my ubuntu from 8.10 to 9.4 and how to use the messenger.

---

### Post by zvacet on 2009-04-22
You can upgrade in several ways:

1. **via net**

system<admin>update manager you will see message that new version is available and choose to upgrade

2. **from alternate CD**

download alternate CD and put it in drive and Ubuntu will recognize it and ask you do you want to upgrade

3. f**rom iso**

download iso and then type in terminal

```
sudo mount -o loop ~/Desktop/ubuntu-8.10-alternate-i386.iso /media/cdrom0
```

if you don´t see dialog then type

```
gksu "sh /cdrom/cdromupgrade"
```

---

