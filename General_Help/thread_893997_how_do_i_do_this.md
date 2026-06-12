---
title: "how do i do this"
date: 2008-08-18
forum: General Help
---

### Post by crashingsucks9 on 2008-08-18
Locate the downloaded rpm file and “cd” into the same directory.

im trying to install lightscribe and it says to do this 

thanks in advance

---

### Post by crashingsucks9 on 2008-08-18
well not download but install

---

### Post by ilovelinux33467 on 2008-08-18
To install rpm packages in ubuntu you need to install alien

```
sudo apt-get install alien
```

Once that is installed do this:

```
sudo alien -i /path/to/package.rpm
```

Look here for more info:
[https://help.ubuntu.com/community/LightScribe](https://help.ubuntu.com/community/LightScribe)

---

### Post by jeepers on 2008-08-18
You need a package called alien to be able to install rpm's. so the easiest way is to do this:

sudo apt-get update
sudo apt-get install alien

then go to where you downloaded the rpm file and run alien <packagename>.rpm. it might be wise to read the manual 1st for switches you might need. so in a terminal run man alien.

cheers

bugger beaten by ilovelinux33467

---

