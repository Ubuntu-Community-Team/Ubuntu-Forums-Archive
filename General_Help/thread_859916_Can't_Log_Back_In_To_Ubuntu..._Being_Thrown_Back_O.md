---
title: "Can't Log Back In To Ubuntu... Being Thrown Back On Login Screen"
date: 2008-07-15
forum: General Help
---

### Post by Rev. Nathan on 2008-07-15
Tried everything in recovery mode, seems to be fine. I enter my password wrong, it just says it's wrong. Enter it right, goes to black for a few seconds, and spits be back onto the KDM Log in screen.

Last thing I did was I was unable to start up Firefox because it gave me a "network configuration" error that prevented it from starting up right and proper. So I rebooting the machine, and now this. Anyone got any wise ideas? I realize this is pretty generic and not information-filled, but I can't really source this problem with the resources I know right now...

---

### Post by cariboo on 2008-07-15
Start up in recovery mode at the prompt type:

```
passwd <user>
```

Where <user> is your user name. To reboot at the prompt type:

```
reboot
```

this should fix your problem.

Jim

---

### Post by bapoumba on 2008-07-15
Or may be you are running out of room somewhere. From the recovery mode, run:
```
df -H
```

---

