---
title: "How much Swap space ?"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by phillw on 2009-07-10
[SIZE=3][FONT=Arial][SIZE=2]Quick one this, I hope !!

System :

80 GB Hard Drive
1 GB RAM
LAMP installed
Learning osCommerce, mail-server, web server etc...
I will have about 10 MySQL databases on it (quite small ones !!)
About 5 users.

System Dual boots with Vista (which currently has 53 GB).

I am re-partitioning this weekend to ...

sda1 25 GB (Vista)
sda3 50? GB (Ubuntu)
sda5 ? GB (Swap)

Is 1 GB swap sufficient, or should I use 2 GB (or a different amount ?!!)

Thanks,

Phillw
[/SIZE][/FONT][/SIZE]

---

### Post by Blacklightbulb on 2009-07-10
1 Gig is sufficient. It won't be using too much swap space. Mine uses as much as 1% swap once in a 1000 sessions. I've got ~1.5 Gig. So yeah 1 Gig is good.;)

---

### Post by PureLoneWolf on 2009-07-10
With that RAM 1gb swap is fine, anywhere between 1 and 2 times the amount of RAM is the recommendation (I went for 2 times, but as with Blacklightbulb, it never gets anywhere near it)

---

### Post by phillw on 2009-07-10
[SIZE=2][FONT=Arial]Thanks ...  1 GB it is going to be !!

):P

Phillw
[/FONT][/SIZE]

---

### Post by Francewhoa on 2009-08-03
Swap recommendations & FAQ aimed at Linux novices at [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

