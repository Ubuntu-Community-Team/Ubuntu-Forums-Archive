---
title: "Is my laptop HDD in danger ?"
date: 2008-04-21
forum: Hardware &amp; Laptops
---

### Post by FredB on 2008-04-21
I've read some months ago about HDD becoming old too fast.

Doing some search, I've get this command line :

```
sudo smartctl -a `mount | grep '/ ' | cut -d' ' -f1 | sed -e 's#[0-9]##'` | egrep 'Cycle|Power'
```

Here is my results :

```

  9 Power_On_Hours          0x0012   099   099   000    Old_age   Always       -       616
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       166
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       8
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       7256

```

I have 7256 / 616 = 11.77 cycle per hours. Is that too much, or very normal ?

Thanks for your comments and info to fix the problem if there is one.

---

