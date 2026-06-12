---
title: "Editing xorg.conf has no effect"
date: 2008-06-01
forum: Hardware
---

### Post by speedkreature on 2008-06-01
The resolutions I'm getting from the built-in nVidia 6100 graphics card are fine.  I'm currently running 1280x1024 which is the maximum resolution my monitor supports however running at a maximum refresh rate of 52Hz is killing my eyes and giving me a headache.  The monitor supports up to 75Hz in this resolution.

I went to the command line and type
```
gtf 1280 1024 75
```
and pasted the result into xorg.conf, but as has typically been my experience, modifications to this file have had no effect.

I've read every bit I could find here that I could pull up concerning low refresh rates.

Please advise.

---

### Post by teaker1s on 2008-10-26
```
sudo gedit /etc/X11/xorg.conf
```

select save file as,will ask if you want to overwrite=yes

---

