---
title: "Ubuntu only recognizes half my ram"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by kvidell on 2005-05-07
For whatever reasn, Ubuntu is only recognizing half of the ram in my laptop.
I have a zippy 2 gigs of ram, but ubuntu only sees about 800 megs of it (less than half, actually)
```
145/kvidell: cat /proc/meminfo
MemTotal:       906656 kB
```When I'm in the bios, it registers the full two gigs, however.

Any ideas?
(NOTE: Problem existed in both Hoary and Breezy)
- Kev

---

### Post by bored2k on 2005-05-07
[QUOTE=kvidell]For whatever reasn, Ubuntu is only recognizing half of the ram in my laptop.
I have a zippy 2 gigs of ram, but ubuntu only sees about 800 megs of it (less than half, actually)
```
145/kvidell: cat /proc/meminfo
MemTotal:       906656 kB
```When I'm in the bios, it registers the full two gigs, however.

Any ideas?
(NOTE: Problem existed in both Hoary and Breezy)
- Kev[/QUOTE]
 linux-386 kernel supports a maximum of 900MB of RAM. Install linux-686, reboot and use that kernel from now on to get your right amount of RAM.

---

### Post by kvidell on 2005-05-07
[QUOTE=bored2k]linux-386 kernel supports a maximum of 900MB of RAM. Install linux-686, reboot and use that kernel from now on to get your right amount of RAM.[/QUOTE]
 Really now? I never realised that. Thank you much!
- Kev

---

### Post by kvidell on 2005-05-07
```
3/kvidell: uname -r && head /proc/meminfo
2.6.10-5-686
MemTotal:      2076268 kB
```Ohh! So much better. Thank you!
- Kev

---

### Post by kvidell on 2005-05-08
[QUOTE=bored2k]linux-386 kernel supports a maximum of 900MB of RAM. Install linux-686, reboot and use that kernel from now on to get your right amount of RAM.[/QUOTE]
 For an Athlon would I do the same thing, or linux-k7 ? (You don't make it sound like it's genderbiased, so I'm curious)
- Kev

---

### Post by bored2k on 2005-05-08
[QUOTE=kvidell]For an Athlon would I do the same thing, or linux-k7 ? (You don't make it sound like it's genderbiased, so I'm curious)
- Kev[/QUOTE]
 Athlon = i686

When you uname -a you'll get that I believe.
I dont even know why there's a k7 package.

---

