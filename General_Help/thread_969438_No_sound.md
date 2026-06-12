---
title: "No sound?"
date: 2008-11-03
forum: General Help
---

### Post by MoscowModder on 2008-11-03
I have Ubuntu 8.10 Intrepid Ibex installed through Wubi on Windows XP Professional.  For some reason, I have no sound whatsoever.  Am I missing the sound driver?  Where could I find it?

Thanks in advance!

---

### Post by shantanu18 on 2008-11-03
You have to install alsa driver. Try this.....
Application>> Accessories>Terminal
```

su

```
give the passward
```

now run this attached script file {just double click} and press Run in terminal.

```


Hope it will help

---

### Post by MoscowModder on 2008-11-04
> **shantanu18 said:**
> You have to install alsa driver. Try this.....
Application>> Accessories>Terminal
```

su

```
give the passward
```

now run this attached script file {just double click} and press Run in terminal.

```


Hope it will help

su????
Is that supposed to be sudo?  Is something missing here?

---

### Post by shantanu18 on 2008-11-04
```

su

```
for login as root

---

### Post by MoscowModder on 2008-11-06
I tried to use *su*, but I gave my own (root) password and it said *su:Authentication failure*.  I tried to open the script and nothing happened.  Do you know what's going on?  What password do I use???

---

### Post by brandon88tube on 2008-11-06
Don't use su as there is no need to. Just use sudo and then your password. Its essentially the same thing.

---

### Post by MoscowModder on 2008-11-17
The script doesn't work.  Now what?

---

