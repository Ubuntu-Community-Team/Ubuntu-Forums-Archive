---
title: "Root password to install Printer"
date: 2010-10-28
forum: Hardware
---

### Post by cookie6 on 2010-10-28
[ATTACH]173810[/ATTACH]

I'm trying to install my wireless printer on Ubuntu 10.10, and it asks for a root password. I put in my login password, but it didn't work.

---

### Post by sisco311 on 2010-10-28
Hi,

Open a terminal (Applications -> Accessories -> Terminal) and run the installer as root:
```
gksu ~/Desktop/lexmark-*i386.deb.sh
```

---

### Post by endotherm on 2010-10-28
it looks like their driver isn;t completely Ubuntu friendly.if gksu won't work, you may have to temporarilly set a root password. unfortunately I am not allowed to tell you how, but you will find it quickly with a search.

---

### Post by sisco311 on 2010-10-28
> **endotherm said:**
> it looks like their driver isn;t completely Ubuntu friendly.if gksu won't work, you may have to temporarilly set a root password. unfortunately I am not allowed to tell you how, but you will find it quickly with a search.

Why? Maybe you should re-read the forum policy: [thread]1486138[/thread] :)

---

### Post by endotherm on 2010-10-28
> **sisco311 said:**
> Why? Maybe you should re-read the forum policy: [thread]1486138[/thread] :)
perhaps. its been a couple years since i got that infraction

Edit: indeed, thanks for the tip

---

### Post by cookie6 on 2010-10-28
Thanks! It worked!

---

### Post by sisco311 on 2010-10-28
You are welcome!

@OP: Don't forget to mark this thread as [SOLVED]. At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" menu, then "Mark this thread as Solved".

---

