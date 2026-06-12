---
title: "Toshiba Satelite A200 Cant Detect Wifi"
date: 2008-06-24
forum: Hardware
---

### Post by victorash on 2008-06-24
I would like to hear from anyone who has Ubuntu and Vista on there Laptops. I have installed Ubuntu 8.04 on a Toshiba Satelite A200 with Vista Home Premium as a Dual Boot option and it works fine..almost. The only problem is Ubuntu cant detect any wireless networks.

If I can get the wireless working I would use Ubuntu more often..

Thanks..

---

### Post by mcabreb on 2009-07-31
I have exactly the inverse problem. In my HP laptop Ubuntu detects all wifi networks but Vista does not. I still have not figured why.

---

### Post by Fire-Eyes on 2009-07-31
> **victorash said:**
> I would like to hear from anyone who has Ubuntu and Vista on there Laptops. I have installed Ubuntu 8.04 on a Toshiba Satelite A200 with Vista Home Premium as a Dual Boot option and it works fine..almost. The only problem is Ubuntu cant detect any wireless networks.

If I can get the wireless working I would use Ubuntu more often..

Thanks..

I had to use 8.10
I could not get wi-fi to work in 8.4
I did not use a duel boot...but I was On a Toshiba and using a netgear wi-fi card
just so you know
I am in no way an expert. Just letting you know what I did.
Good Luck

---

### Post by mdmarmer on 2009-07-31
You need to determine what wireless card you have -- or atleast tell us the exact model of your laptop -- I think at least 3 different wireless cards were used in different models of A200

[https://help.ubuntu.com/8.04/internet/C/wireless.html](https://help.ubuntu.com/8.04/internet/C/wireless.html)

To identify your card enter
 lspci
as root and look for a line about wireless

lspci -v
or
lspci -vv

will give you more data if needed

Mike

---

### Post by w_1_n_d on 2009-08-02
i had the same problem, i had a toshiba satellite a200 with an atheros 5006ex wireless card. i just upgraded to ubuntu 9.04, in this version of ubuntu they use a driver called ath5k and now my cards works perfectly. try it, what do you got to lose?:KS:KS:KS:KS

---

