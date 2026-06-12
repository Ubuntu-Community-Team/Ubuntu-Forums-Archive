---
title: "Radeon HD 4850"
date: 2009-12-03
forum: Hardware
---

### Post by pyrofyr on 2009-12-03
I read in the compatibility list that it's compatible however whenever trying to install the proprietary drivers I get the following error:

SystemError: installArchives() failed

Results of: ([Done because of this]("https://help.ubuntu.com/community/BinaryDriverHowto"))
lspci | grep VGA
> 01:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4870]


---

### Post by Yellow Pasque on 2009-12-04
Yes, the RadeonHD4870 is supported.
> SystemError: installArchives() failed
From what I can tell on a web search, this indicates a problem with apt, and can occur when installing any package if the the cache is out of date.
```
sudo apt-get update
```

---

### Post by pyrofyr on 2009-12-04
Ran the update and tried again, no dice. Also checked to see if there was an updated xorg driver, but it was the same one I have installed.

---

