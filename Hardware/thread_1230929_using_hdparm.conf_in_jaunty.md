---
title: "using hdparm.conf in jaunty"
date: 2009-08-03
forum: Hardware
---

### Post by acranox on 2009-08-03
I've got a few values I'd like to set with hdparm to my disk.  I can run the commands manually, and they work fine. 
#hdparm -M 128 /dev/sda

However I've set /etc/hdparm.conf according to the man page, but the changes aren't being applied at boot.
For example I've added this to the file:

```
/dev/sda {
        acoustic_management
        spindown_time = 120
}
```

I did a little looking, and /etc/init.d/hdparm doesn't exist, it seems that it's supposed to be called from udev, and the files look okay.
/lib/udev/rules.d/85-hdparm.rules 
/lib/udev/hdparm

But the settings aren't getting applied on boot.  Any ideas?

--Peter

---

### Post by mikewhatever on 2009-08-05
ls -l /etc/hdparm.conf
-rw-r--r-- 1 root root 4793 2009-01-09 14:24 /etc/hdparm.conf

Here's mine, and it's not executable, which possibly explains why it is not run at boot.

---

### Post by acranox on 2009-08-09
That doesn't really make any sense.  conf files don't need the execute bit set, a program just reads in the values to determine what arguments to run with.

---

