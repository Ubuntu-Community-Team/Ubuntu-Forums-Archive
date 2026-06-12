---
title: "Can I install Wubi on the Win7 RC?"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by Fzang on 2009-07-09
Now that it's an RC it's almost 100% stable, so I was wondering if it's regarded as "safe enough to try".

I've also heard some horror stories about having to add the boot entries manually to BCD. Do I really have to do that? Not that it's a problem...

PS: Does Wubi boot faster/slower?

---

### Post by Partyboi2 on 2009-07-09
Hi, from what I have read you will need to add an entry to bcd or you could try [[COLOR=Blue]this[/COLOR]]("http://www.clububuntu.com/2009/01/how-to-solve-windows-7-and-ubuntu-810.html"). 
As for performance you will find that having Ubuntu on its on its partition will be better then using wubi.

---

### Post by Fzang on 2009-07-09
I already have Ubuntu installed on a separate partition. The problem is that something broke and now all my icons are gone. I want to reinstall but I don't have an external backup source and I have a TON of music I wouldn't want to lose.

I'm using Ubuntu for basics, customising and digital art in GIMP. Would I feel an impact on performance?

---

### Post by Partyboi2 on 2009-07-10
When I was using wubi I found that my boot up time was a lot slower, as for general performance it was not to bad.
If you have plenty of free space currently for your Ubuntu installation its  possible  to backup your music or other data before doing a reinstall, you would need to boot a ubuntu live cd and use Partition Editor to shrink down your current ubuntu partition and then create a new one next to it. Then copy over your music and data to the new partition, then you can reinstall Ubuntu.

---

