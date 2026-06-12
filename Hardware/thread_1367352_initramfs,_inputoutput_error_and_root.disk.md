---
title: "initramfs, input/output error and root.disk"
date: 2009-12-29
forum: Hardware
---

### Post by DarkDarkness on 2009-12-29
Hello everyone.
I have an updated ubuntu. installed with wubi besides my windows.
Since the last system update i cant boot my ubuntu.
I have found out that there is an error with the root.disk file. which is probably the ubuntu root partition file created by wubi.
The file is in /host/ubuntu/disks but ls doesnt show it.
I have tried to mount this file, but i get an input / output error and cant even backup my files there.
What can i do?
Thanks, and sorry about my English.
(Lenovo SL500)


Solved using chkdsk /f in windows.

---

