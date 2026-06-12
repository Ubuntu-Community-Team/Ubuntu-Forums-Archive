---
title: "HELP! g++ dependency issue..."
date: 2008-08-01
forum: General Help
---

### Post by absguitarist on 2008-08-01
I have the debians for g++-2.95 and libstdc++2.10-dev, but when i run the package installer on either they need the other to install. What do i do?

---

### Post by NikoC on 2008-08-01
What if you go to your terminal and type:

sudo apt-get install build-essential

That should install both...

Cheers.

---

### Post by absguitarist on 2008-08-01
thanks a lot! wish i understood linux better...

---

### Post by prshah on 2008-08-01
> **absguitarist said:**
> I have the debians for g++-2.95 and libstdc++2.10-dev, but when i run the package installer on either they need the other to install. What do i do?

Or, if you want to use the downloaded files and not re-download them, you can use the command```

sudo dpkg -i g++-2.95.deb libstdc++2.10-dev.deb
```

---

### Post by the-angry-scientist on 2011-01-22
I can't thank you enough prshah!!!!
I have internet on my droid..(I rooted mine...still no custom rom for mine to utilize wifi tether...yet)
So I have to download packages on my phone and transfer to my pc..I tried to install but I kept getting dependency problems...

It wanted to redownload them online...and that frustrated me because I don't have internet on my pc, but the sudo dpkg -I [package].deb works great! Thanks a million!!!

---

