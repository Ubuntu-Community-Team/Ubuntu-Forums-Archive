---
title: "CD reading extremely slow"
date: 2005-08-20
forum: Hardware &amp; Laptops
---

### Post by Jenda on 2005-08-20
Hello, Ubuntu folks!

I'm having a little trouble with my CD drives. Ripping a single CD takes about forty minutes, sometimes up to eighty (ripping or extraction for burning). I am really sorry to say this, but in Windows, which I obviously had before, it never took so long. I'm pretty sure my DMA is on.

And now that we're on the subject, what is Overburn and Burnfree?

Thanks in advance,
Jenda

---

### Post by tseliot on 2005-08-20
[QUOTE=Jenda]Hello, Ubuntu folks!

I'm having a little trouble with my CD drives. Ripping a single CD takes about forty minutes, sometimes up to eighty (ripping or extraction for burning). I am really sorry to say this, but in Windows, which I obviously had before, it never took so long. I'm pretty sure my DMA is on.

And now that we're on the subject, what is Overburn and Burnfree?

Thanks in advance,
Jenda[/QUOTE]
1) Check that the DMA is enabled by typing in Terminal or Konsole:
sudo hdparm -d /dev/cdrom

2) "Overburn" = when you burn over the capacity of a storage media (CD-R, DVD-r, etc.). For example you can write 75 min on a CD with 74 min capacity.

3) Burnfree, Burnproof, etc. are "functions" which prevent the buffer underrun error (i.e. if you don't enable it it's more likely that you will have to throw your CD away).

---

### Post by Jenda on 2005-08-21
[QUOTE=tseliot]1) Check that the DMA is enabled by typing in Terminal or Konsole:
sudo hdparm -d /dev/cdrom

2) "Overburn" = when you burn over the capacity of a storage media (CD-R, DVD-r, etc.). For example you can write 75 min on a CD with 74 min capacity.

3) Burnfree, Burnproof, etc. are "functions" which prevent the buffer underrun error (i.e. if you don't enable it it's more likely that you will have to throw your CD away).[/QUOTE]
 OK, thanks, tseliot. I have DMA on on both of my drives, and yet it took about 90 minutes to rip half a CD yesterday using GnomeBaker. The CD was damaged, but I've ripped it before and it never took near as long.
Burnproof will come in handy, since when I tried to burn the thing from the oggs in on my hd, it only got halfway through and got the buffer underrun error.

---

