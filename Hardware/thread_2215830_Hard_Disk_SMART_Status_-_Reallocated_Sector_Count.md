---
title: "Hard Disk SMART Status - Reallocated Sector Count"
date: 2014-04-08
forum: Hardware
---

### Post by PartisanEntity on 2014-04-08
Hi there,

Luckily I have not had many drives fail so far so I am not quite sure how bad this drive is failing.

Anyone with some experience concerning these values care to chime in? On a scale of 1 - 10 where is the worst case, is this a 9?

[ATTACH=CONFIG]251843[/ATTACH]

Thanks

---

### Post by nick96 on 2014-04-09
Back up any personal data that you need. It will eventually die like that. Wouldn't know how long it would last but I've known a guy whose hard drive in the laptop died after a few weeks when I checked it.

---

### Post by frostschutz on 2014-04-09
reallocated and pending sectors? a smart self-test will most likely fail. get a replacement for that disk.

---

### Post by PartisanEntity on 2014-04-09
I tried the short test which passed without any issues.

The advanced test however is breaking off midway and not completing, looks like imminent death. Shame really as this disk is hardly used.

---

### Post by sudodus on 2014-04-09
Yes, it looks bad, I would not rely on that disk. Maybe it can last for a while for testing purposes after marking the bad sectors.

```
sudo e2fsck -cf /dev/sdxy
```

---

