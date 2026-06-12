---
title: "New app does not launch during boot."
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by sci-fi guy on 2008-12-29
I installed [miredo]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=miredo") for IPv6 functionality, but it does not launch during boot (it's in the init folders, though) It works fine if I launch it manually.

---

### Post by kunixos on 2008-12-29
```
System > Preferences > Sessions
```
Then under the 'Startup Programs' tab, add 'miredo'.

Let me know how this works!

---

### Post by sci-fi guy on 2008-12-29
It needs to be launched as root, and should be launched as part of init/upstart/whatever

---

### Post by albinootje on 2008-12-29
> **sci-fi guy said:**
> I installed [miredo]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=miredo") for IPv6 functionality, but it does not launch during boot (it's in the init folders, though) It works fine if I launch it manually.

The order of launching it could be wrong.
You can look at this :
```

ls -la /etc/rc2.d/

```
To see when miredo wants to start.

Assuming that Ubuntu, even though upstart supposedly doesn't do runlevels anymorem, still "emulates" using runlevel 2 for normal start up.

---

### Post by sci-fi guy on 2008-12-29
miredo wants to start in rc3. Should I copy the link to rc2?

---

### Post by cariboo on 2008-12-29
You could also use update-rc.d to install the script, type in a terminal

```
sudo update-rc.d <basename> defaults
```

Where <basenmae> = the program you want to start automagically on boot.

Jim

---

