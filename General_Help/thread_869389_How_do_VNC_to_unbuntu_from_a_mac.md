---
title: "How do VNC to unbuntu from a mac"
date: 2008-07-24
forum: General Help
---

### Post by Bubs on 2008-07-24
?

How can I remote desktop into my ubuntu box from a mac computer on the same network?

Found one thread that gives a little info but doesn't help.  Thread is closed now so I'll start a new one.

so assuming I know very little how would I do this?


I Actually want to use the monitor from my ubuntu box with my mac since the mac has all my 3D and graphic apps on it.  but I still use the ubuntu box for various things.  So I want to be able to remote desktop in and control it.  I would like to be able to share files back and forth too if thats possible...

bubs

---

### Post by ryanhaigh on 2008-07-28
[VNC]("https://help.ubuntu.com/community/VNC") is the standard way of accessing ubuntu remotely. There are others such as xdmcp but VNC will probably do everything you need. Im sure you can find a vnc viewer if there is not one included by default apparently osx also has a built in vnc server so it probably has a view also.

I don't know how macs do file sharing but I assume they can use samba/windows file sharing, in which case you will want to look at [this]("https://help.ubuntu.com/community/SettingUpSamba") for setting up shares on your ubuntu machine.

---

