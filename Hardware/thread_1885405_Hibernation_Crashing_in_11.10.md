---
title: "Hibernation Crashing in 11.10"
date: 2011-11-23
forum: Hardware
---

### Post by jasoncruz98 on 2011-11-23
Hibernation worked perfectly fine in 11.04. Ever since I  upgraded to 11.10, my laptop (Acer Aspire) keeps crashing when it's  hibernating. I have no clue why. Any ideas?


  At first it seemed to only happen between 6a-noon (US Eastern time), but this morning it happened earlier.
  (PS. I checked /var/log/syslog but I'm not sure what I'm looking for.  I thought something might jump out at me as an obvious error in  hibernating or coming out of it, but nothing seemed unusual. I'm a bit  of a newbie in this area so I might be missing something in lines upon  lines upon lines)

---

### Post by Paddy Landau on 2011-11-29
Is your /home folder encrypted? (You probably would have chosen that option when you installed. If you're not sure, open Nautilus; navigate to [FONT=Fixedsys]/home[/FONT]; press Ctrl-H to view hidden files. If you see a folder called [FONT=Fixedsys].ecryptfs[/FONT], your home folder is encrypted.)

Hibernation does not work with encrypted home folders, because in that case the swap partition is also encrypted and thus you cannot resume from hibernation.

---

