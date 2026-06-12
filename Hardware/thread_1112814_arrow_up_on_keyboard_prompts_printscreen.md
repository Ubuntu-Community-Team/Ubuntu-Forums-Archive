---
title: "arrow up on keyboard prompts printscreen"
date: 2009-04-01
forum: Hardware
---

### Post by restless on 2009-04-01
hey

I just upgraded from 8.04 to 8.10 and some issues arose.

the keyboard configuration isn't working properly and when i click on "pg up" it gives me "/" and when i click on arrow up it prints screen.

i already found that is a common problem, with a workaround, but the one i found on [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/254840](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/254840)
which says to modify
xorg.conf by adding 
```

Section "ServerLayout"
 Identifier "Default Layout"
 Screen "Default Screen"
 Inputdevice "Generic Keyboard"
 Inputdevice "Configured Mouse"
EndSection

```

doesn't work for me

any ideas please?
thanx

lor

---

### Post by restless on 2009-04-01
please!!!

anyone knows how to fix this issue??

i also tried to follow this method
[https://bugs.launchpad.net/ubuntu/+bug/255167](https://bugs.launchpad.net/ubuntu/+bug/255167)
and again it didn't work...

any ideas?

---

