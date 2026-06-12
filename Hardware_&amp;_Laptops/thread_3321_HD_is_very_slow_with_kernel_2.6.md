---
title: "HD is very slow with kernel 2.6"
date: 2004-11-05
forum: Hardware &amp; Laptops
---

### Post by toto on 2004-11-05
My hard drive is very slow with the 2.6 kernel of Ubuntu. With a 2.4, there is no problem.
Example : 

root@ubuntu:/home/toto # hdparm -Tt /dev/hda
/dev/hda:
 Timing buffer-cache reads:   916 MB in  2.00 seconds = 457.84 MB/sec
 Timing buffered disk reads:   14 MB in  3.07 seconds =   4.56 MB/sec

Normally, with an other kernel, my default value for the Timing buffered disk reads is 25 MB/sec.

What's wrong ?
I have a DELL inspiron 8200

Could you help me ? Is it a problem with the kernel ? Or maybe with fstab ?

Thanks

---

### Post by kil on 2004-11-07
[QUOTE=toto]My hard drive is very slow with the 2.6 kernel of Ubuntu. With a 2.4, there is no problem.
Example : 

root@ubuntu:/home/toto # hdparm -Tt /dev/hda
/dev/hda:
 Timing buffer-cache reads:   916 MB in  2.00 seconds = 457.84 MB/sec
 Timing buffered disk reads:   14 MB in  3.07 seconds =   4.56 MB/sec

Normally, with an other kernel, my default value for the Timing buffered disk reads is 25 MB/sec.

What's wrong ?
I have a DELL inspiron 8200

Could you help me ? Is it a problem with the kernel ? Or maybe with fstab ?

Thanks[/QUOTE]


the problem is cdrom drive. put a cd in it and all works fine...
I put in a cd when I boot in waiting for a real bug fix

When cd is read, you can remove it, Ubuntu working fine to.

---

### Post by toto on 2004-11-12
Yes, it works ! 
Thank you for your answer !


Is something missing in their kernel ? Maybe a driver ?

toto

---

### Post by Razvan on 2004-11-14
whoouw! now im happy! MY disk reads 53.6 mbps :-) 

(without workaround) \\:D/   :-P  :wink:

---

