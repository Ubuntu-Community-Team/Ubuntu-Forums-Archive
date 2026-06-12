---
title: "No sound with USB Logitech headset/mic"
date: 2009-09-26
forum: Hardware
---

### Post by chris1950 on 2009-09-26
Plugged in headset, checked speaker prefs, set all volunes, tried all device options rebooted,but sound only comes from the laptop speaker. Headset is _not muted _,set  at max volume. Have no idea it mic works or not.:confused:

---

### Post by awk on 2009-09-26
have you tried adjusting the mixer settings?
```
# alsamixer
```

---

### Post by chris1950 on 2009-09-26
> **awk said:**
> have you tried adjusting the mixer settings?
```
# alsamixer
```

copied & pasted code nothing happened.
chris@compaq:~$ # alsamixer
chris@compaq:~$ cd /
chris@compaq:/$ # alsamixer
chris@compaq:/$ sudo # alsamixer
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
chris@compaq:/$

code chris@compaq:~$ alsamixer
not listed -see screen shot
is listed in volume properties-screen shot

---

### Post by chris1950 on 2009-09-27
bump

---

