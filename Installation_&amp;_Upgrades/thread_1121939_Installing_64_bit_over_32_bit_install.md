---
title: "Installing 64 bit over 32 bit install"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by Mi5 on 2009-04-10
After using the 32 bit version of Ubuntu I want to give the 64 bit version a try, can I install the 64 bit version without reformating the hard drive or losing the programs currently installed

---

### Post by drs305 on 2009-04-10
You have to do a clean install to upgrade to 64-bit. I was going to provide the commands for importing your currently installed apps but will have to research it a bit. I can tell you the new repositories will contain only apps compatible with your new 64-bit system.

The command to save your currently installed apps is:
```

sudo dpkg --get-selections | grep -v "deinstall&#8221; >$HOME/Desktop/installed-packages 

```

The command I was going to supply would recreate your current system's apps exactly but don't know if that is wise when transitioning from 32 to 64 since the command also removed apps.

---

### Post by Mi5 on 2009-04-11
Thanks

---

