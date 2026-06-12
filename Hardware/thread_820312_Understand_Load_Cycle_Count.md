---
title: "Understand Load_Cycle_Count"
date: 2008-06-06
forum: Hardware
---

### Post by stchman on 2008-06-06
Hello all, I was reading and after I intalled smartmontools I did the following command.

```
sudo smartctl -a /dev/sda | grep Load_Cycle_Count
```

The last number was 4423.  Is this number high?  I just bought the laptop 2 weeks ago.

Does this mean I have have had 4423 load cycles in 2 weeks?  That is about 8K a month.  That is about 96000 a year.  What do these numbers mean?  Is the average hdd 600,000 load cycles?

I did the command again and the number did not change.

Does the disc store the number of cycle counts?

Help me to understand.

Thanks.

---

### Post by sdennie on 2008-06-06
The disk does store the information and, 4400 in 2 weeks is nothing to worry about at all.  That gives the disk 6 years until Load_Cycle_Count could become a *possible* point of failure.  I would check these numbers again in a few months and, as long as they still seem reasonable, they are nothing to worry about.

---

### Post by sergiom99 on 2008-06-06
@stchman, you could check it after several hours of use and see the Load_Cycle_count variation.
Use this and you'll get the timestamp on screen.
```
date; sudo smartctl -a /dev/sda | grep Load_Cycle_Count
```

@vor: no te vi postear en el Argentina LoCo Team (puede ser que este equivocado). Tu participación realmente sería de utilidad, ya que tenes profundos conocimientos de laptop. Te esperamos.

---

