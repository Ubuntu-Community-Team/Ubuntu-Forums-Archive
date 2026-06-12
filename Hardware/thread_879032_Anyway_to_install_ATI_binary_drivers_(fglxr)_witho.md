---
title: "Anyway to install ATI binary drivers (fglxr) without rebooting?"
date: 2008-08-03
forum: Hardware
---

### Post by Harry Muscle on 2008-08-03
Is there anyway to install the ATI binary (or restricted) drivers (fglxr) without rebooting?  Basically I would like to install them while running the Ubuntu Live CD so that I can test some stuff without actually installing Ubuntu to the hard drive.

Thanks,
Harry

P.S.  Here's what I've tried and it didn't work:

- install fglxr package (using EnvyNG)
- run "sudo killall gdm"
- run "sudo killall Xorg"
- run "sudo rmmod radeon"
- run "sudo gdm"

it still seems to want to use the Mesa drivers when I did the above (glxinfo shows Mesa), but doesn't load them properly since I unloaded the radeon module.

---

### Post by jocko on 2008-08-03
> **Harry Muscle said:**
> Is there anyway to install the ATI binary (or restricted) drivers (fglxr) without rebooting?  Basically I would like to install them while running the Ubuntu Live CD so that I can test some stuff without actually installing Ubuntu to the hard drive.

Thanks,
Harry

P.S.  Here's what I've tried and it didn't work:

- install fglxr package (using EnvyNG)
- run "sudo killall gdm"
- run "sudo killall Xorg"
- run "sudo rmmod radeon"
- run "sudo gdm"



it still seems to want to use the Mesa drivers when I did the above (glxinfo shows Mesa), but doesn't load them properly since I unloaded the radeon module.

What happens if you try to load the fglrx module?
```
sudo modprobe fglrx
```

---

### Post by Harry Muscle on 2008-08-03
> **jocko said:**
> What happens if you try to load the fglrx module?
```
sudo modprobe fglrx
```

I get:

FATAL: Error running install command for fglrx

Thanks,
Harry

---

