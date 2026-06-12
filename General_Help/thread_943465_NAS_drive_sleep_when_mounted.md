---
title: "NAS drive sleep when mounted"
date: 2008-10-10
forum: General Help
---

### Post by jobsonandrew on 2008-10-10
I have a network drive which i managed to mount (automatically at boot via fstab) using:
```
\\<ip_of_network_drive>\<sharename> /media/<mountpoint> cifs nounix 0 0 
```
which works great, but im wondering... Normally, after 5 mins of inactivity, the network drive will go into sleep mode (spin the disk down and become dormant).

My question is, will Linux overide this sleep mode and keep the drive awake for as long as it is mounted?

Cheers

---

