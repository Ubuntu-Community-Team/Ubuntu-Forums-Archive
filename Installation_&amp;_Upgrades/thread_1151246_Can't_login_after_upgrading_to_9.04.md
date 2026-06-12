---
title: "Can't login after upgrading to 9.04"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by MedianMajik on 2009-05-06
I'm trying to help a friend who upgraded from 8.10 to 9.04 and can no longer login.  The default settings were username: user and password: user.

Does Jaunty have some default login settings that I'm not aware of?  Any help is greatly appreciated.  Note that this guy is a total noob to linux and needs as much "plain english" as possible.  I haven't had a chance to use Jaunty yet so I'm not much help.

---

### Post by kas782000 on 2009-05-08
I am having the exact same problem after upgrading from 8.04 to 9.10.  My user name was my name and I used my own personal password which are apparently both wrong now.  I also tried to log in with user for the name and password and had no luck.

---

### Post by black_shadow on 2009-05-08
Hi

When Ubuntu starts to boot press ESC (you have to be quick as it is only available for approx 5 secs) to get the Grub menu and select (recovery mode), this will drop you into a root account here you can do the following to reset your password :-

```
passwd username 
```

The enter your now password twice and reboot as normal this shouls allow you to login again.

Regards Michael

---

