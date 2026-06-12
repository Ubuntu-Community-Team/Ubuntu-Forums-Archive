---
title: "Get Ink Levels, sudo needed?"
date: 2011-09-16
forum: Hardware
---

### Post by nshiell on 2011-09-16
I need to get the ink levels for my Dad's USB printer on Ubuntu 11.04.
My dad installed **ink** which does show levels. I wanna write a GUI for it but I can only run the command with sudo on my profile.
Can I change this to run without sudo rights, or anyone know of a GUI to use?

```

nicholas@ubuntu:~$ sudo ink -pusb
ink 0.5.1 (c) 2010 Markus Heinz

Canon iP5200

Black:                         70%
Photoblack:                   100%
Yellow:                       100%
Magenta:                      100%
Cyan:                         100%
nicholas@ubuntu:~$ ink -pusb
Could not access '/dev/usb/lp0' or '/dev/usblp0'.
Could not get ink level.
nicholas@ubuntu:~$ 

```

Any thoughts?

---

### Post by agillator on 2011-09-16
Check the file permissions of the files (devices) the program can't access. Your problem is probably one of ownership.

---

### Post by nshiell on 2011-09-18
How can I change permissions on the devices, how can I find out which device it uses?

---

### Post by hybenz on 2012-02-04
> **nshiell said:**
> I need to get the ink levels for my Dad's USB printer on Ubuntu 11.04.
My dad installed **[ink]("http://www.inkjetsuperstore.com/")** which does show levels. I wanna write a GUI for it but I can only run the command with sudo on my profile.
Can I change this to run without sudo rights, or anyone know of a GUI to use?


same question.. can it run without sudo rights? did you have any problems after installing ink?

---

