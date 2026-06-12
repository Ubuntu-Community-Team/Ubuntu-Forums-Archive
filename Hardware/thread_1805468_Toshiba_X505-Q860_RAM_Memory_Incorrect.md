---
title: "Toshiba X505-Q860 RAM Memory Incorrect"
date: 2011-07-16
forum: Hardware
---

### Post by jadonchristensen on 2011-07-16
Hello, I own the Toshiba X505-Q860 and the RAM reports correctly as 4GB in the BIOS, Windows 7, etc. However, in Ubuntu 11.04 32bit it is showing as 2.9/3 GB. I read about this issue on older models that was later corrected by a Ubuntu update. 

What should I do to correct this problem?

Should I submit this as a bug somewhere?

Thank you

---

### Post by jadonchristensen on 2011-07-16
Found the solution here:
[http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/)

---

### Post by foresthill on 2011-07-16
Hmmm. I run 4 gb in my notebook but it always shows up as 3. I always assumed it was because of my on-board graphics using the extra gig.

No matter though. I have never seen Ubuntu actually use more than one gig of RAM anyway. My system usually uses 300 mb's or less at any given time.

---

### Post by jadonchristensen on 2011-07-16
> **foresthill said:**
> Hmmm. I run 4 gb in my notebook but it always shows up as 3. I always assumed it was because of my on-board graphics using the extra gig.

No matter though. I have never seen Ubuntu actually use more than one gig of RAM anyway. My system usually uses 300 mb's or less at any given time.

I posted the fix above. This is for the 32bit version.

```
sudo apt-get install linux-generic-pae linux-headers-generic-pae
```

then do

```
sudo reboot
```

---

