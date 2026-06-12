---
title: "Can't find intel 945 driver"
date: 2009-07-12
forum: Hardware
---

### Post by Loud SIlence on 2009-07-12
Could someone please help me find an intel 945 GM express chipset family driver for Ubuntu 9.04 because I've searched google and the intel website but can't fine one.

Thanks in advance.

---

### Post by IcarusR on 2009-07-12
I have a Toshiba laptop with  Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller which is supported (& works) out of the box. 
No extra drivers required. So It is fair to assume that it would also be supported & work out of the box.
Why are you looking for a driver ?? Does it not work ??

---

### Post by IcarusR on 2009-07-12
Just found this thread on the forum, which would suggest there are some issues with Intel graphics on Jaunty.
There are instructions as to possible fixes....
[http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582")

---

### Post by Sturmeh on 2009-07-12
```
$ sudo apt-get install xserver-xorg-video-intel
```

But like they said, it's installed by default if you installed it directly on there.

You might want to read [this]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") however if using Jaunty.

---

### Post by cabosixpack on 2009-07-12
Hi, all, i have the same graphic card, and have it working 90%, only thing i can't get to work is the s-video out, IcarusR do you have it working?

---

### Post by Loud SIlence on 2009-07-14
It does have a driver, but I thought it might be outdated because on windows i can play Crysis on it, but on ubuntu I can't even watch a youtube video without it being laggy! So is the default driver the latest driver?

---

### Post by kirbyno1 on 2009-08-10
Im having the same issues. When scrolling in firefox for example it gets really skippy. I cant even enable the "Normal" or "Extra" visual effects under "Appearance Preferences". Not sure what to do.

---

