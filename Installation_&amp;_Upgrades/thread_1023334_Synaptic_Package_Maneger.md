---
title: "Synaptic Package Maneger"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by pshown on 2008-12-27
When Trying to open Package Manager I am getting this error:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
I have no idea how to correct this. Can anyone help?

---

### Post by howefield on 2008-12-27
The error is giving the answer

Run the following command in a terminal (Applications > Accessories > Terminal)

```
sudo dpkg --configure -a
```

---

### Post by taurus on 2008-12-27
Close synaptic first.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by pshown on 2008-12-27
Thank you guys. I am just a newbe here and should have realized I had to run the command with the sudo prefix.

---

