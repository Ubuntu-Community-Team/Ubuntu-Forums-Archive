---
title: "Unable to hibernate"
date: 2008-07-16
forum: Hardware
---

### Post by bas1 on 2008-07-16
Hi,

I have an HP dv4419us Pavilion notebook that refuses to hibernate. I've had issues with hibernation in Ubuntu ever since I first started using it (version 7.04). I ran the /etc/acpi/hibernate.sh script, and it spat out some errors.

```
brandon@brandon-laptop:~$ sudo /etc/acpi/hibernate.sh
ifdown: interface eth0 not configured
ifdown: interface eth1 not configured
Allocated buffer at 0x2010 (base is 0x0)
ES: 0x0201 EBX: 0x0000
 * Shutting down ALSA...                                                 [ OK ] 
 * Saving the system clock
/etc/acpi/hibernate.sh: line 39: echo: write error: Cannot allocate memory
Laptop mode disabled, not active.
Function not supported
 * Setting the system clock
Ignoring unknown interface eth0=eth0.
Ignoring unknown interface eth1=eth1.
 * Setting up ALSA...                                                    [ OK ] 
FATAL: Module acpi_sbs not found.
FATAL: Module acpi_sbs not found.
brandon@brandon-laptop:~$
```

Anyone know of a fix? Thanks for any help! :)

---

### Post by bas1 on 2008-07-17
bump

---

### Post by dwang on 2008-07-17
I'm not sure about 7.04, but in 8.04 (hardy), hibernate.sh is deprecated.  You should use pm-suspend and pm-hibernate.

Dave

---

### Post by herakles29 on 2009-01-17
I am in this trouble too
I have a PC Desktop with ubuntu hardy and a Nvidia Geforce 7050
I think it is a Nvidia restricted drivers related problem
also pm-hibernate/suspend doesn`t work


any solution or suggestion?

---

### Post by linux_tech on 2009-01-17
make sure swap is enabled, load different kernel, try different video driver

---

### Post by herakles29 on 2009-02-26
> **linux_tech said:**
> make sure swap is enabled, load different kernel, try different video driver

thanx for suggestion but swap is unabled as you can see:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19128   153645628+  83  Linux
/dev/sda2           19129       19457     2642692+   5  Extended
/dev/sda5           19129       19457     2642661   82  Linux swap / S
```

and I also update to Intrepid to see what happens
but last time I tried to hibernate I had troubles with my hda1 with loss of the superblock etc..
(also suspend doesn't work)

original drivers seems to be the only ones working good with nvidia cards

I also found a blog that seems to focus on the problem but the given solution (configuring the AGP) doesn't fit with my card type..
[http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/]("http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/")

any other suggestion?
thanx

---

