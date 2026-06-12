---
title: "Specifying bad blocks manually with mkfs"
date: 2011-10-13
forum: Hardware
---

### Post by itix on 2011-10-13
Hey forums!
I am trying to reinstall my old laptop with ubuntu oneiric. The problem is that I know that I have a couple of blocks that make my hard drive fail quite badly. I want to exclude those blocks when creating a file system but [COLOR="DarkGreen"]-c[/COLOR] or [COLOR="DarkGreen"]-c -c[/COLOR] with [COLOR="DarkGreen"]mkfs[/COLOR] doesn't work... it fails at block 1448576 with both and the hard drive start making a lot of noise. I know that the block is bad so I was wondering if you can exclude it (and perhaps future others) manually?

Tried googling but nothing :(

Thanks

---

### Post by westie457 on 2011-10-13
> **itix said:**
> Hey forums!
I am trying to reinstall my old laptop with ubuntu oneiric. The problem is that I know that I have a couple of blocks that make my hard drive fail quite badly. I want to exclude those blocks when creating a file system but [COLOR="DarkGreen"]-c[/COLOR] or [COLOR="DarkGreen"]-c -c[/COLOR] with [COLOR="DarkGreen"]mkfs[/COLOR] doesn't work... it fails at block 1448576 with both and the hard drive start making a lot of noise. I know that the block is bad so I was wondering if you can exclude it (and perhaps future others) manually?

Tried googling but nothing :(

Thanks
Hello with a hard drive making a lot of noise do not even think of using it because it is very likely to fail by seizing solid and burning out the on board motors. Far better to get another hard drive and use that instead.

---

### Post by itix on 2011-10-13
Naah. It has been like that for over a year... It is always block 1448576 that makes it do a lot of noise (tiny clicks and other odd sounds). It won't seize solid if it hasn't done so for a year. The annoying thing is that if I don't specify the bad blocks the file system try to write to them and fails which requires me to do a hard reset (or norwegian reset as we in sweden call them).

So the question still remain.

---

### Post by itix on 2011-10-13
There is an option -l which will specify bad blocks in a file but I still haven't found how that file is supposed to look like... which format etc

---

