---
title: "Can any Windoz driver be installed?"
date: 2012-01-17
forum: Hardware
---

### Post by maspai on 2012-01-17
Hi all. I once installed Windoz wifi driver via ndisgtk (ndiswrapper). Can any other driver be installed this way, too? Eg. Windoz driver for mobile, modem, VGA etc. Thanx for replies.

---

### Post by carl4926 on 2012-01-17
No
First determine if you really need to use ndiswrapper, because it's a last resort IMO

---

### Post by adityamagadi on 2012-01-17
you can try using wine to run windows applications ...

---

### Post by MoreOrLess on 2012-01-17
ndiswrapper installs "windoz" xp wireless drivers. That's it. Are you having other issues with a device?

---

### Post by maspai on 2012-01-17
> **MoreOrLess said:**
> ndiswrapper installs "windoz" xp wireless drivers. That's it. Are you having other issues with a device?

Mostly I don't have internet connection, so I must do everything offline (such as installing drivers etc.), and I have some windoz drivers in my harddisk.

I used ndisgtk to install windoz wifi driver offline when I installed my Lubuntu 10.10 on my Acer Aspire 522 netbook with Broadcom wifi. I had to get the wifi first so then I could install other drivers such as ATI VGA online where I had internet connection.

BTW having Linux on my netbook, I must get connected to internet to install everything :(.

---

### Post by carl4926 on 2012-01-17
Post the result of

```
lspci -nnk
```

---

### Post by Mark Phelps on 2012-01-17
First of all, there are no "Windoz" drivers. So -- NO.

Second, the only "Windows" drivers that can be used in Linux are those you have used already -- with NDISwrapper.

And, if anyone tells you to try using Wine -- forget it.  Wine can NOT be used to install Windows drivers.

---

