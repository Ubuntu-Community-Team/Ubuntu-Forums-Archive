---
title: "Deciphering fglrxinfo"
date: 2009-05-23
forum: Hardware
---

### Post by harujai on 2009-05-23
I'm running Jaunty with an ati HD 3650 card. Currently i'm trying to work on installing the 9.5 catalyst drivers. 9.4 installed fine but there were many graphics issues. I'm working on a new Ubuntu installation so there's no improper unintsallation causing this. I build the jaunty files and install them. Then after running aticonfig --initial -f  i check to see if the drivers are installed properly with fglrxinfo and i get:

harujai@harujai-desktop:~$ fglrxinfo
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Value in failed request:  0x1
  Serial number of failed request:  24
  Current serial number in output stream:  24

Thoughts? I have no idea what any of that means.

---

