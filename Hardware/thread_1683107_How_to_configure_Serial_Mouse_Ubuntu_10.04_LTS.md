---
title: "How to configure Serial Mouse Ubuntu 10.04 LTS?"
date: 2011-02-07
forum: Hardware
---

### Post by KingBongo on 2011-02-07
Hi. This is driving me nuts. Since HAL has been replaced with UDEV it is very hard to configure and set up a Serial Mouse. Before all you had to do was to change a little in xorg.conf and voila! Well, those were the days!

I am running minimal Ubuntu 10.04 LTS with Fluxbox and LXDE installed. I installed the package "gpm" and tried 

```
inputattach --microsoft /dev/ttyS0
```

in several ways: 

1. If I write it directly in terminal (no GUI) nothing happens, I get a bunch of text with "Killed" at the end. I know when the command is active and working the corresponding (virtual) console should lock up. At least it has before.

2. If I try putting it in the file " /etc/rc.local" like I have seen in some places, the computer hangs during boot.

Can anybody help me out here please!

---

### Post by KingBongo on 2011-02-12
Hellooooooo?

Is it really the case that the issue with serial devices hasn't been resolved yet? Then why switch to UDEV? I have seen several posts on the web where people are having problems with serial stuff.

---

### Post by KingBongo on 2011-02-15
bump

---

### Post by bpb_21 on 2011-02-23
I need help too.  See specifically [http://www.gossamer-threads.com/lists/mythtv/users/427612]("http://www.gossamer-threads.com/lists/mythtv/users/427612") (how does he know what port the serial mouse is on?).  When I try this nothing happens (during boot or otherwise).

---

### Post by Perkins on 2011-07-07
You generally need to put an & on the end of anything in rc.local, otherwise bootup will wait for the command to finish before continuing.

There is also a --daemon paramater for inputattach that makes it run in the background as a detached process.

Are you not using a GUI at all on this system then?

---

