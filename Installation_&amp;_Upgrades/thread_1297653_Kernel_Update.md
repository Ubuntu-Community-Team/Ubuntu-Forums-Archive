---
title: "Kernel Update"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by running_rabbit07 on 2009-10-22
I just updated to kernel 2.6.28-16 and now my VBox doesn't work. How do I get the VBox to work with the new kernel?

Thanx.

---

### Post by Bachstelze on 2009-10-22
> **running_rabbit07 said:**
> I just updated to kernel -16 and now my VBox doesn't work. How do I get the VBox to work with the new kernel?

Thanx.

You need to recompile your vbox kernel modules.

---

### Post by running_rabbit07 on 2009-10-22
> **Bachstelze said:**
> You need to recompile your vbox kernel modules.

How do I make that happen?

Thanx for the quick response.

---

### Post by running_rabbit07 on 2009-10-22
Ok, I figured it out. Thanks again for the quick response.

For other who may have the same issue ```
rabbit@Rabbid-Rabbit:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for rabbit: 
 * Stopping VirtualBox kernel module                                             *  done.
 * Removing old VirtualBox netflt kernel module                                  *  done.
 * Removing old VirtualBox kernel module                                         *  done.
 * Recompiling VirtualBox kernel module                                          *  done.
 * Starting VirtualBox kernel module                                             *  done.
rabbit@Rabbid-Rabbit:~$ 

```

---

### Post by botfish on 2009-10-22
I tried the instructions posted by running_rabbit07 and got the following:

~$ sudo /etc/init.d/vboxdrv setup
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}

/etc/init.d/vboxdrv does not have a setup option

I'm running virtualbox-ose

---

### Post by running_rabbit07 on 2009-10-22
You may have to reinstall then. I am using the latest VBox downloaded from the Sun site.

---

