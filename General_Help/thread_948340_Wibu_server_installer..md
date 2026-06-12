---
title: "Wibu server installer."
date: 2008-10-15
forum: General Help
---

### Post by MvdM on 2008-10-15
Hello,

Is it possible to edit the wibu.exe file so it installs ubuntu server edition?

regards!

MvdM

---

### Post by ago on 2008-10-15
I do not think that the Ubuntu server uses the Live CD and the alternate ISO is not supported at the moment. Also I would not run a server on wubi because the filesystem is not as robust as the native ones. But if you really wish to, you can run wubi and before rebooting edit 

c:\ubuntu\install\custom-installation\preseed.cfg

Replace ubuntu-desktop with ubuntu-standard. That will install a minimal setup (console mode) with apt, from there you can connect to the web and install any additional server packages you wish

---

### Post by MvdM on 2008-10-15
I have an EeeBox and i don't want to change the partitions because the 3th partition is a recovery partition. so i want to run a server that's why i want to instal wibu server

---

