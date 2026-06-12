---
title: "I need to update Linux kernel to latest version using Ubuntu. How?"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by NS RAO on 2009-05-13
I am trying to update the latest version of Ubuntu Linux to the latest Linux kernel so I can use ndiswrapper. I am unsure how to install the kernel, however. How can I do this so I can get ndiswrapper running under Ubuntu?

---

### Post by chemicalfan on 2009-05-13
There should be instructions with the kernel you've downloaded, but it'll centre around (all under sudo):
./configure
make clean
make
make install

But check the documentation before you proceed!

---

### Post by tarps87 on 2009-05-13
This should do both

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```

---

### Post by doru001 on 2011-12-18
Should not be like this? 
```

sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by ubix on 2011-12-18
> **doru001 said:**
> Should not be like this? 
```

sudo apt-get update
sudo apt-get dist-upgrade

```

```

sudo apt-get update && sudo apt-get dist-upgrade

```

Both of the above are correct. The last is using AND syntax which means execute both commands if the first one was successful.

---

### Post by oldos2er on 2011-12-18
Closed, necromancy.

---

