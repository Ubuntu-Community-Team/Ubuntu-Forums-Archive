---
title: "Panasonic KX-MC6000 printer/scanner"
date: 2011-10-27
forum: Hardware
---

### Post by tommpogg on 2011-10-27
Hi,

I have got a networked Panasonic printer/scanner.
I managed to install the printer drivers by following [this thread]("http://ubuntuforums.org/showthread.php?t=1598250").
Now, I cannot figure out how to scan.

I am using Ubuntu 10.10 64-bits

Should I install another driver? Where can I find it?

Thank you

---

### Post by tommpogg on 2012-01-03
Suddenly the printer prints very slowly (a page every 4 minutes or so).

 Can anybody provide some help?

---

### Post by mörgæs on 2012-01-03
Moved to the hardware forum.

---

### Post by librechick on 2012-01-03
This may not be helpful to you now although I do have a suggestion for the future. 

Panasonic like most other manufacturers doesn't provide good support for systems designed around free software. The problem is the company doesn't cooperate with the free software community and so drivers can't be fixed, updated, or improved upon. It can cause maintenance headaches for users. Users often have to manually reinstall printer drivers after an upgrade and frequently enough these aren't available as you are reliant on a commercial entity who would rather not support a discontinued product. Some times the product hasn't even been discontinued and they still don't provide updated drivers. You are truly at the mercy of the  manufacturer for support.

Even though hacks can work around the problems many times it is generally a cumbersome solution. Do you want to spend three hours figuring out how to get it working or would you rather just get a printer that worked?

Some of HP's printers are free software compatible and they make it fairly easy (comparison wise) to find them. They have a list on their driver web site. That list indicates for each printer if it is dependent on a non-free plug-in or firmware.

I can also recommend [http://www.thinkpenguin.com/](http://www.thinkpenguin.com/) if you prefer not research it. This company only sells free software compatible products.

---

### Post by tommpogg on 2012-01-05
> **librechick said:**
> Panasonic like most other manufacturers doesn't provide good support for systems designed around free software. The problem is the company doesn't cooperate with the free software community and so drivers can't be fixed, updated, or improved upon. It can cause maintenance headaches for users.

Thank you for the explanation. Now I can see why I had such an hard time trying to install the drivers.

> **librechick said:**
> 
Users often have to manually reinstall printer drivers after an upgrade and frequently enough these aren't available as you are reliant on a commercial entity who would rather not support a discontinued product.
I have (partially) solved my problem by reinstalling the drivers.
If someone is interested, I have used this cups web interface: [http://localhost:631/admin](http://localhost:631/admin) (see[ this thread]("http://ubuntuforums.org/showthread.php?t=1482510&page=2")).

> **librechick said:**
> 
Even though hacks can work around the problems many times it is generally a cumbersome solution. Do you want to spend three hours figuring out how to get it working or would you rather just get a printer that worked?

Some of HP's printers are free software compatible and they make it fairly easy (comparison wise) to find them. They have a list on their driver web site. That list indicates for each printer if it is dependent on a non-free plug-in or firmware.

I can also recommend [http://www.thinkpenguin.com/](http://www.thinkpenguin.com/) if you prefer not research it. This company only sells free software compatible products.It wasn't my choice to buy a printer not supported for linux. I am using my company's one. Anyway, I will take your suggestion into account if I will need to buy a printer.

---

