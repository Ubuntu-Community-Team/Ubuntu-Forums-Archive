---
title: "slow transfer speeds between hard drives"
date: 2008-10-09
forum: General Help
---

### Post by onesojourner on 2008-10-09
I have been transfering large amounts of data between hard drives recently and the speeds I am getting seem extremely slow. The initial speeds might get up to about 40mb but then it trails off to about 20mb on really large transfers. Is 40mb a second normal for 2 sata hdds?

---

### Post by Vaphell on 2008-10-24
Your results are still good compared to mine... If you have similar problem to mine, your drives don't get UDMA enabled or something like that

I have 2 sata drives and nautilus showed 1.7MB/s when copying big files (from /home ext3 to ntfs on second hdd). Burning dvd is literally faster than moving files between HDDs. Seriously, wtf? -_-
I managed to increase speed to stellar 4MB/s by blacklisting general_ide or something like that.
There are few threads about painfully slow SATA and they indicate some problem with libata which unified pata, sata and scsi drivers some time ago, around gutsy/feisty i think?

---

