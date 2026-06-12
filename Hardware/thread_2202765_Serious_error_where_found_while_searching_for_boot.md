---
title: "Serious error where found while searching for /boot"
date: 2014-01-30
forum: Hardware
---

### Post by Fuji_in_Japan on 2014-01-30
Hello all,

I am getting a message like Serious error where found while searching for /boot.  I always press i for ignore.

How do I tell what the serious error is?  And I guess from there what is the next step?

Thanks in advance,
Dave

---

### Post by Bashing-om on 2014-02-02
Fuji_in_Japan; Hi !

Try a "simple" file system check/repair:
terminal codes:
```

sudo touch /forcefsck
sudo shutdown -r now

```
which will set a parameter to check the file system at next reboot, 
shutdown is that next reboot.

Let the file system check complete, boot to the desk top and once more (re-)boot.

Are you still seeing errors ?

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

