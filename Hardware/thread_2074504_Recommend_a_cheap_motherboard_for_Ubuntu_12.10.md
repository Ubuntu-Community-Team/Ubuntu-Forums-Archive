---
title: "Recommend a cheap motherboard for Ubuntu 12.10?"
date: 2012-10-21
forum: Hardware
---

### Post by mark2741 on 2012-10-21
I have a PC that I built about 5 or 6 years ago that has never worked well with Ubuntu. It has a GigaByte motherboard with an AMD x2 chip from around that era. 

Although I have since moved on to using laptops, I recently installed Ubuntu 12.04 on this older desktop for my son and it was unbearably slow. And wireless kept dropping. I eventually gave up and switched to Xubuntu and it runs much better, but it does freeze from time to time and the wireless keeps dropping.

I live near a MicroCenter and they always have cheap motherboard/CPU combos on sale. I'm thinking if I can get something for under $100 then it will be worth upgrading this desktop, but I wanted to check to make sure what I buy is 100% compatible with Ubuntu. Can anyone recommend a motherboard/cpu combo that is cheap but will run 12.10 100% compatible?

---

### Post by Yellow Pasque on 2012-10-22
What socket? Please post output from the following command:
```
sudo dmidecode
```

Random freezing could indicate problems with overheating, a faulty/cheap PSU or bad RAM, so make sure it's not overheating and let memtest run overnight to check the RAM.

---

