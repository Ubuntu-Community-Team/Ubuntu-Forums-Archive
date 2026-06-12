---
title: "Activate PAE kernel to identify more than 4GB RAM?"
date: 2011-12-10
forum: Hardware
---

### Post by smartcard on 2011-12-10
How can I update my Lubuntu to identify 10GB RAM that I have in my PC?

---

### Post by wolfen69 on 2011-12-10
```
sudo apt-get install linux-generic-pae linux-headers-generic-pae
```

---

### Post by Rodney9 on 2011-12-10
You could use the Lubuntu 64 Bit

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by smartcard on 2011-12-10
> **wolfen69 said:**
> ```
sudo apt-get install linux-generic-pae linux-headers-generic-pae
```

Thanks, this worked for me.

---

### Post by MoreOrLess on 2011-12-10
Just beware that individual apps are still limited in how much memory they can use, so if you have a program that you want to devote a lot of RAM to, like gimp or virtualbox, you're better off biting the bullet and doing a fresh 64-bit install.

---

### Post by smartcard on 2011-12-10
> **MoreOrLess said:**
> Just beware that individual apps are still limited in how much memory they can use, so if you have a program that you want to devote a lot of RAM to, like gimp or virtualbox, you're better off biting the bullet and doing a fresh 64-bit install.

Thanks for the suggestion, now I am on 64 bit

---

