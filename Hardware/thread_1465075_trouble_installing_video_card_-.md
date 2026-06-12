---
title: "trouble installing video card :-\"
date: 2010-04-29
forum: Hardware
---

### Post by =Ninja= on 2010-04-29
Hi, hopefully I have put this in the right place :P

I'm having some trouble trying to install drivers for my ATI Radeon x800. I've downloaded the driver from AMD but when I try to run it I get this message:

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-21-generic; make sure that the version is being
correctly set by --iscurrentdistro

the driver seems to unpack and then gets to that point and stops and deletes all the temp files... Not really sure where to go from here

---

### Post by Bucky Ball on 2010-04-29
Are you using this kernel?

2.6.31-21-generic

---

### Post by =Ninja= on 2010-04-29
according to uname -r, yes... 
sorry if I'm a bit slow, am a bit of a n00b with linux.

---

### Post by Bucky Ball on 2010-04-30
One thing you don't mention is the machine. Is it 64bit or 32? Because the driver seems to be 64bit.

---

