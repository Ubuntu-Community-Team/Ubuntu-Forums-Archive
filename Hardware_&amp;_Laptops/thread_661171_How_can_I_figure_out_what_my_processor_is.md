---
title: "How can I figure out what my processor is?"
date: 2008-01-07
forum: Hardware &amp; Laptops
---

### Post by dbsoundman on 2008-01-07
All right, here's my problem. I'm trying to reinstall Swiftfox, but Automatix is being dumb and won't give me the option to install Swiftfox now that I've uninstalled it. In the Automatix install, it automatically picks the right Swiftfox for my processor. However, that one is not working, so I need to manually install it. To do that, I need to download the right installer for my processor. I tried picking AMD64, but that one won't start up now that I've got it installed. So either something else is wrong, or I need to match my processor to my Swiftfox build. I suppose this is a hardware issue..sort of. Any suggestions?

-Dan

---

### Post by kebes on 2008-01-07
To get some info about your processor, you can type this in a terminal:
```
cat /proc/cpuinfo
```

However when you need to decide between 32-bit or 64-bit software, it depends what version of Ubuntu you installed. You can get a hint about which one is installed by doing:
```
uname -a
```

It's quite possible that (even if you have an AMD64 processor) you installed Ubuntu 32-bit (which is fine, by the way), in which case you should just be using the standard x86/32-bit packages.

---

### Post by dbsoundman on 2008-01-07
Thanks! It appears I have an Athlon XP processor. As far as I know I do not have a 64 bit installation. I never did do some research to find out what the difference is between 32 and 64 bit actually, I should probably do that...

-Dan

---

### Post by Yellow Pasque on 2008-01-07
Athlon XP is not 64-bit compatible, so it's a moot point.

---

### Post by stoodleysnow on 2008-01-07
You can also find it by going to system-Administration-System Monitor (tab on left)

---

