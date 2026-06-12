---
title: "install CD issues"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by amazoohwawa on 2009-11-05
I bought a new Acer Extensa 4630Z with Linpus preinstalled. the problem is that it does not recognize the CD which i just burned with 9.10 on it.

Anyone can tell how to fix this??


Thanks :)

---

### Post by dhavalbbhatt on 2009-11-05
> **amazoohwawa said:**
> I bought a new Acer Extensa 4630Z with Linpus preinstalled. the problem is that it does not recognize the CD which i just burned with 9.10 on it.

Anyone can tell how to fix this??


Thanks :)
It seems like a bad ISO image and/or a bad CD. Did you check the CD for defects as well as perform the MD5 checksum?

---

### Post by amazoohwawa on 2009-11-05
checked the CD and it all seems fine. i dont what the MD5 is?? Can u help?

---

### Post by dhavalbbhatt on 2009-11-05
Here is a good howto on burning a ISO file and checking MD5

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by amazoohwawa on 2009-11-05
okay, so i checked the MD5 checksum and it gave me a long number. what does that mean?

---

### Post by dhavalbbhatt on 2009-11-06
> **amazoohwawa said:**
> okay, so i checked the MD5 checksum and it gave me a long number. what does that mean?
That long number is a hash number. You compare that with the hash number for the Ubuntu you are trying to install (for example, if you are trying to install Ubuntu 9.10 32 bit, it will have its unique hash number). You can look up the hash number for your install at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes). If both numbers match, then it means that your MD5 is OK.

---

