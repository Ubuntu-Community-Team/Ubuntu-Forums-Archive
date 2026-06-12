---
title: "Kernel Modules to remove"
date: 2008-08-05
forum: General Help
---

### Post by MikeyDL on 2008-08-05
I was installing vmware workstation 6.0 in the middle of the pl script when I did a stupid Ctrl+Alt+Del and shutdown the system.

Trying to do the install process again but the script tells me to remove the following kernel modules:

    * vmmon
    * vmblock
    * vmnet

How do you remove those...figure it might be simple rm -r command but not sure where they are located.

Thanks,

---

### Post by pauper on 2008-08-06
Well, you don't actually remove modules as in delete, but rather unload them.
To view whether some particular module is currently inserted you can run these
commands. It returns zero if no matches found.

```
grep vmmon /proc/modules
```

You can group them together:

```
grep -E '(vmmon|vmblock|vmnet)' /proc/modules
```

Or simply preview all at once:

```
lsmod
```

To remove modules use:

```
sudo modprobe -r vmmon vmblock vmnet
```

---

### Post by MikeyDL on 2008-08-06
**THANKS!**

I knew this was going to be a bit of a mess for me to figure out at my current ability level!

---

