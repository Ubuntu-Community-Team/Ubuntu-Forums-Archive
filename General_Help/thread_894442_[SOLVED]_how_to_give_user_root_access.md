---
title: "[SOLVED] how to give user root access?"
date: 2008-08-19
forum: General Help
---

### Post by yarozar on 2008-08-19
Can someone help me how do I give to a normal user root access level/rights? Not just 'sudo' but exactly all permissions on the system. Thanks!

P.S.: I know it is dangerous and Ubuntu tells everywhere not to do this ever but I need this.

---

### Post by tuxxy on 2008-08-19
You could try,

```
su
```

Use your root password

---

### Post by kellemes on 2008-08-19
> **tuxxy said:**
> You could try,

```
su
```

Use your root password

There isn't a root password on the default Ubuntu install..

Use..
```
sudo -i
```

---

### Post by bingoUV on 2008-08-19
> **tuxxy said:**
> You could try,

```
su
```

Use your root password

yes. And if you have not yet set your root password,
```
sudo -s
```works fine too.

---

### Post by tuxxy on 2008-08-19
Sorry yes I forgot to add that it must be enabled first.

---

### Post by yarozar on 2008-08-19
You have misunderstood me.

I want to give user "User" such rights that he be able to manipulate (editing, deleting, etc) files which belong even to root **without** using sudo ...

---

### Post by Vivaldi Gloria on 2008-08-19
> **yarozar said:**
> I want to give user "User" such rights that he be able to manipulate (editing, deleting, etc) files which belong even to root **without** using sudo ...

[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)
[https://help.ubuntu.com/community/RootSudo#Enabling%20the%20root%20account](https://help.ubuntu.com/community/RootSudo#Enabling%20the%20root%20account)

---

### Post by yarozar on 2008-08-19
Clear. Please close topic.

---

### Post by Vivaldi Gloria on 2008-08-19
> **yarozar said:**
> Clear. Please close topic.

You can mark the thread as [SOLVED] using the thread tools.

---

