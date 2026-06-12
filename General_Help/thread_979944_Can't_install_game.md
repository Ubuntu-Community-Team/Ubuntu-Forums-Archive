---
title: "Can't install game?"
date: 2008-11-12
forum: General Help
---

### Post by 5h4dy on 2008-11-12
Hello. I've been using Ubuntu now for a total of 2 days. I love it and I plan to use it avidly. I've been trying to install Tremulous but I cannot, it says I do not have permission. So I googled it and someone had the same problem, the answer was to login as root to install it. So I tried that, and it said the Admin isn't allowed to login[via the front door] so how do I login as Root? Or how to I set my account permissions equal to root?

I was able to get to the install part, but it said I didn't have privilages to install to usr/local/games/ ?

---

### Post by Ryadt on 2008-11-12
Use sudo to gain administrative right.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
```
sudo apt-get install tremulous
```

---

### Post by 5h4dy on 2008-11-12
> **Ryadt said:**
> Use sudo to gain administrative right.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
```
sudo apt-get install tremulous
```


So in the future, if I get problems like this again, simply sudo in the console and it should override it?

---

### Post by Ryadt on 2008-11-12
Yep.

---

### Post by oldos2er on 2008-11-12
Please read [https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html)

---

