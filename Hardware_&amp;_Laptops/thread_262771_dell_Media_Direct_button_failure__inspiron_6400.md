---
title: "dell Media Direct button failure / inspiron 6400"
date: 2006-09-22
forum: Hardware &amp; Laptops
---

### Post by alemora on 2006-09-22
i just installed ubuntu 6.06 on my inspiron 6400. The original partition table for my computer was as follows:
1.Dell Restore
2.Dell utilities
3.C (Windows XP) partition

using the partitioner on the installer now i have 
1.Dell restore / primary (left it untouch)
2.Dell utilities / primary (left it untouch)
3.Windows  / primary (resized)
4. Extended with 3 logical partitions
   4.1 swap 
   4.2 filesystem for linux
   4.3 fat32 for sharing between ubuntu and windows

I set up the grub and now a ihave a double boot available of Windows XP and Ubuntu. 

The problem is that when i try to go to the media direct utility  just by pressing the Media Direct button before starting the computer i keep getting thrown to the Grub screen where i HAVE 
to select either Linux or Windows, being not able to get into media direct. 

Does anyone know how i can solve this problem?????

Thanks for the help...

Grettings from Costa Rica!!!!!

---

### Post by Konlii on 2006-12-18
Basically, the original Dell-installed MBR is actually made up of two sectors.  The second sector is what loads when you hit the MediaDirect button.  Since you overwrote the entire MBR with Grub, this obviously won't work anymore.

More information on MediaDirect can be found at [http://www.goodells.net/dellrestore/mediadirect.htm]("http://www.goodells.net/dellrestore/mediadirect.htm").

---

