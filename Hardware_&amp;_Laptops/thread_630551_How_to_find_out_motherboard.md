---
title: "How to find out motherboard"
date: 2007-12-03
forum: Hardware &amp; Laptops
---

### Post by johnaaronrose on 2007-12-03
A really elementary question. What is the Linux command to find out PC's motherboard manufacturer and name? I've tried hwinfo -- with various parameters. I've tried Hardware Information (from Preferences menu). Ive tried googling. I need to know to see if my BOS s/w needs updating. Help please.

---

### Post by eggdeng on 2007-12-03
> BOS s/w 

Do you mean BIOS??
```
sudo lshw
``` should tell you.

```
sudo lshw > /home/your_username/hw.txt
```
will export to a file so you can search the output more easily.

---

