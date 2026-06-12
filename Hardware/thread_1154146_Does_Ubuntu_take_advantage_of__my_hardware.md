---
title: "Does Ubuntu take advantage of  my hardware?"
date: 2009-05-09
forum: Hardware
---

### Post by Heeter on 2009-05-09
Hi all,

I am wondering: Today, we all have some sort of quad cores, multiples amounts of DDR2 ram, multi HDs in RAID arrays, 24" dual monitors and so on and so forth.

Does Ubuntu 9.04 64bit actually take advantage of all this?

Thanks

Heeter

---

### Post by Barry Carroll on 2009-05-09
Cores:  Sure - the default kernel supports SMP so your cores will be recognised and used.  Performance, like other OS, won't be multipled by 4.

It'll depend on the application whether you'll see any appreciable performance increases.  Some particular application like certain games won't speed up, but others will.  It's really like asking 'how long is a piece of string' unfortunately.

Memory: If you want more than 4GB then go for a 64-bit OS and as long as your BIOS can detect it then so will Ubuntu less any that has been used for shared graphics memory or other memory 'holes'.

RAID is something that I have not used personally but it's something that is set up outside of the OS, so as long as your raid controller is supported then this should be transparent to the underlying OS.

Multiple monitors will be supported if your graphics adapter supports them and I believe that the displays configuration applet in Jaunty will allow you to manage them from there.

---

### Post by Heeter on 2009-05-09
Great Thanks for your input, Barry Carrol. much appreciated.




Heeter

---

