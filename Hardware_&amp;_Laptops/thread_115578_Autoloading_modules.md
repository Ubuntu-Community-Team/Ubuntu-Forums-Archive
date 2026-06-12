---
title: "Autoloading modules"
date: 2006-01-10
forum: Hardware &amp; Laptops
---

### Post by marcantonio on 2006-01-10
Hey all,

I'm a little new to Ubuntu, but not Linux.  I'm trying to figure out how Ubuntu is loading my ethernet driver.  The interface is ath0 and the driver is ath_pci.  I can find no reference to either in /etc (grep -r ath0 /etc), except for ath0 in /etc/network/interfaces.  Looking through the init scripts I can see how the interface is brought up because it's listed in the interfaces file, but how and at what point, is modprobe ath_pci being run?

Thanks a lot,
Marc

---

### Post by jasmuz on 2006-01-10
Did you check under /etc/moules file?

---

### Post by healychan on 2006-01-10
You can read /etc/modules or "cd" into directory /etc/modprobe.d/ then do "ls".

The modules loaded at boot time should be shown.

---

### Post by marcantonio on 2006-01-11
[QUOTE=healychan]You can read /etc/modules or "cd" into directory /etc/modprobe.d/ then do "ls".

The modules loaded at boot time should be shown.[/QUOTE]

That's the thing, neither my driver (ath_pci) or my interface (ath0) are mentioned in /etc/modules, /etc/modprode.d/*, /etc/hotplug, etc...

So what is telling Ubuntu to load that module?:confused:

---

### Post by marcantonio on 2006-01-12
Bump... somebody's got know how Ubuntu does this.  Enlighten me! :smile:

---

### Post by marcantonio on 2006-01-12
In case anyone is interested, it is hotplug that is load the module.  I was interested in the "how", though.

The function load_drivers() is called from /etc/hotplug/pci.agent which, in turn, loads all the modules listed in /lib/modules/$KERNEL/modules.pcimap.

Now my OCD is statisfied... :D

---

