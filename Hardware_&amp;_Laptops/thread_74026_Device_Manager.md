---
title: "Device Manager"
date: 2005-10-10
forum: Hardware &amp; Laptops
---

### Post by j0eb0b on 2005-10-10
I have just put togther a machine running Ubuntu 5.04 that is pretty much functional at this point.  One question.  There is almost no useful information contained in device manager about any of the components in my system.  The peripheral devices are identified by name but I can't find any of the information that would normally be displayed is Windows XP device manager.  Is this a flaw in 5.04 or is there something that I need to do to populate device manager information.  I can't even figure out how much hard drive space has been used by the installation.

All ideas are welcome.

THanks,
Joe

---

### Post by mlomker on 2005-10-10
I'm more familiar with the command-line than the graphical tools (they also vary depending upon the shell that you are using whereas the command-line doesn't).

disk space:

```

df -h

```

Some other useful information:

```

lspci
lsusb
dmesg | less

```

---

