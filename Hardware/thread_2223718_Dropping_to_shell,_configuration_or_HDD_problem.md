---
title: "Dropping to shell, configuration or HDD problem?"
date: 2014-05-12
forum: Hardware
---

### Post by steven_taylor2 on 2014-05-12
Hi All,

I know that there have been many posts regarding "Gave up waiting for root device", but I cant find the answer to my specific situation. Upon booting, I get the black screen followed by...

[COLOR=#ff0000]Gave up waiting for root device. Common problems:
   -Boot args (cat /proc/cmdline)
      -Check rootdelay= (did the system wait long enough?)
      -Check root= (did the system wait for the right device?)
   -Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/742ce143-aa25-4b8a-802e-dd36e0151427 does not exist. Dropping to a shell![/COLOR]

BUt this only happens about every other time I boot. The file at[COLOR=#ffff00] [/COLOR][COLOR=#800000]/dev/disk/by-uuid [/COLOR]does, in fact, exist. Sometimes it boots fine, other times I get the error. So how can I determine if this is a configuration error, or my hard drive starting to fail? THe system is an 8 year old gateway with a 500gb HDD.

THanks,
Steve

---

### Post by mörgæs on 2014-05-12
Hi, welcome to the fora.
Which release of Buntu are you using?

---

