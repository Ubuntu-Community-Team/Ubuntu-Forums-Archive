---
title: "Failed install w/ new HDD"
date: 2010-08-05
forum: Hardware
---

### Post by RoyT on 2010-08-05
My HDD on my laptop was getting a lot of errors so I replaced it with a new one. I installed 10.04 from a CD without errors. When I restarted I got:

error: out of disk.
grub rescue>

Would it be possible for the entire install to complete without ever testing whether the disk was compatible and not bad?
I replaced an IDE with a PATA drive.

---

### Post by serpentracer on 2010-08-05
I wonder if it has anything to do with your Bios not recognizing your drive?

---

### Post by RoyT on 2010-08-05
Probably not. I dug out my 8.04 CD and installed it. Works fine. So, this seems to be related to 10.04. 

BTW, I am running a Dell inspiron 600m

---

### Post by serpentracer on 2010-08-06
I just recently installed a new 160g pata drive in my compaq presario laptop in place of it's IDE drive without issues.  in fact, linux sees all 160g when windows only sees it as 80 or so.
I hate windows so badly

the guy at the computer store said pata drives will work in any ide drive's place.

---

### Post by cascade9 on 2010-08-07
> **serpentracer said:**
> I just recently installed a new 160g pata drive in my compaq presario laptop in place of it's IDE drive without issues.  in fact, linux sees all 160g when windows only sees it as 80 or so.
I hate windows so badly

the guy at the computer store said pata drives will work in any ide drive's place.

Just FYI, IDE/PATA (and a few other terms) are pretty much the same thing. 

> The current Parallel ATA standard is the result of a long history of incremental technical development, which began with the original AT Attachment interface, developed for use in early [PC AT]("http://en.wikipedia.org/wiki/PC_AT") equipment. The ATA interface itself evolved in several stages from [Western Digital]("http://en.wikipedia.org/wiki/Western_Digital")'s original **Integrated Drive Electronics (IDE)** interface. As a result, many near-synonyms for ATA/ATAPI and its previous incarnations exist, including abbreviations such as *IDE* which are still in common informal use.

[http://en.wikipedia.org/wiki/Integrated_Drive_Electronics](http://en.wikipedia.org/wiki/Integrated_Drive_Electronics)

---

### Post by RoyT on 2010-08-07
Apparently, my problem was a result of a bad install off the CD. Starting with the old 8.04 CD I have upgraded via Update Manager all the way to 10.04 and everything seems to be working fine.

Thanks for the answers.

---

### Post by serpentracer on 2010-08-07
> **cascade9 said:**
> Just FYI, IDE/PATA (and a few other terms) are pretty much the same thing. 



I know.
it's a dead interface.  sata  is now the norm

---

