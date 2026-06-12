---
title: "I've installed DamnSmallLinux on my 486 but my hdd is FULL..."
date: 2008-08-15
forum: General Help
---

### Post by Sycron on 2008-08-15
I have installed DSL on my 486DX2 66mhz , 20MB RAM and everythung works exelent except one strange thing.

I have a 365MB HDD. After installing DSL free space was about 200MB ... and i don't know for what reasons now I have 0.00MB free.. i delete some files... make free space but free space it's gonna eaten and i don't know why. Please help me! I want a webserver but i don't have space to put my htmlfiles...

---

### Post by bingoUV on 2008-08-15
```

cd /
du -h --max-depth=1

```

Do this to figure out biggest directories. Maybe some log files have become very large.

---

### Post by Sycron on 2008-08-15
How can I see the output like with more? I mean if the rows are exceding 25 i want the scrolling to stop until i press a key... is this possible? thank you.

**/usr** has 185MB .... here should be the problem.

---

### Post by DGortze380 on 2008-08-15
> **Sycron said:**
> How can I see the output like with more? I mean if the rows are exceding 25 i want the scrolling to stop until i press a key... is this possible? thank you.

**/usr** has 185MB .... here should be the problem.

du -h --max-depth=1 | more

---

### Post by insane_alien on 2008-08-15
```
du -h --max-depth=1 | less
```

should solve that, or the more one above.

---

### Post by Sycron on 2008-08-15
> **insane_alien said:**
> ```
du -h --max-depth=1 | less
```

should solve that, or the more one above.

Thanks it works with *less*.

---

### Post by Sycron on 2008-08-15
How do I remove firefox in DSL .. since i don't use it because it's to bloated for my 486 ?

How do I install localepurge on DSL ? With apt-get i get some dependencies errors...

---

