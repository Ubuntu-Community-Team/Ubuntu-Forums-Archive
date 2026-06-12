---
title: "[SOLVED] Can I install Ubuntu 8.04 without a format?"
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by viral1991 on 2008-12-26
Hello, everyone. :) 

I use Win XP currently & want to install Ubuntu as a second OS. My PC has four NTFS partitions with XP in the C: drive. The G: drive has 11 GB free out of 31 GB. So, I am going to utilize that space for Ubuntu.

So, my question is, Can I install Ubuntu without formatting the G: drive?

Thanks in advance. :KS

---

### Post by logos34 on 2008-12-26
> **viral1991 said:**
>  G: drive has 11 GB free out of 31 GB. So, I am going to utilize that space for Ubuntu.

So, my question is, Can I install Ubuntu without formatting the G: drive?

no, you have the shrink it and format the resulting ~11 gb as ext3 (and linux-swap)

Try the option 'Guided--use largest continuous space' or 'Guided--resize windows'...If neither of them use the G: drive, then choose the 'manual' option, shrink G:, then turn the 11 gb into an primary **extended** partition...Make a 1 Gb /swap (logical, linux-swap) and the rest to / (logical, ext3)

---

### Post by viral1991 on 2008-12-27
> **logos34 said:**
> no, you have the **shrink it and format the resulting ~11 gb** as ext3 (and linux-swap)



Thanks for the help. :)

So, does that mean that the existing 20 GB in G: will remain as it is?

---

### Post by namdung on 2008-12-27
Yes, the remaining data will be safe if u do it carefully and correctly.

Good luck.

---

### Post by viral1991 on 2008-12-27
> **namdung said:**
> Yes, the remaining data will be safe if u do it carefully and correctly.

Good luck.

Thanks. I am ready to install Ubuntu now. :)

---

### Post by viral1991 on 2008-12-28
I have installed Ubuntu now, & it's working perfectly! :KS Thanks for the help, both of you. :)

---

