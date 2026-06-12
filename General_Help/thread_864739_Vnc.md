---
title: "Vnc"
date: 2008-07-19
forum: General Help
---

### Post by waiwai933 on 2008-07-19
I've enabled remote desktop through system-preferences-remote desktop. How would somebody VNC into my machine? Thanks.

---

### Post by steveneddy on 2008-07-19
They need to know your IP address.

Go to ipchicken.com and get your IP address.

In a terminal, if they are running Linux or Ubuntu also, they would type:

```
vncviewer [COLOR="Blue"]your.ip.address.here[/COLOR]:0
```

[COLOR="Blue"]vncviewer[/COLOR] is the name of the application that allows one to see the other PC.

Your IP address is the location of the viewed PC.

[COLOR="Blue"]:0[/COLOR] means to view the live screen.

If it were a [COLOR="Blue"]:1[/COLOR], that is a separate login that they can use separately while you use your login.

Linux is a multiuser OS, and this is the way that you can multi use your system.

EDIT:

Your IP will be something like 

65.123.123.345

in that format.

You can get a friend with Windows to install a free VNC viewer and they can see your from their machine.

---

