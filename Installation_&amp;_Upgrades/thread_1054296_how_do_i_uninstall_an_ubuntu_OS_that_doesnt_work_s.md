---
title: "how do i uninstall an ubuntu OS that doesnt work so i can try again?"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by polskimoose on 2009-01-29
i currently dual boot xp and ubuntu on a dell desktop computer, and i NEED to uninstall ubuntu, but when i boot to ubuntu it doesnt work. what do i do?

---

### Post by Pumalite on 2009-01-29
If you want to try again; all you have to do is boot your Live CD, install, go 'Manual' and use the old Ubuntu partitions. You can ignore /swap.

---

### Post by polskimoose on 2009-01-29
see, my live CD doesnt work, which is the reason i need to uninstall this OS. i've tried making more, and they never work.

SO, i was gonna try and use wubi as my second try.

---

### Post by Pumalite on 2009-01-29
OK; then get Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn to disk and boot from it. Erase the Ubuntu partitions.
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
If you need to fix your Windows MBR; you can use your Installation CD or Super Grub:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by polskimoose on 2009-01-29
whats the difference between the ubuntu live cd and the gparted cd?

will it install ubuntu or some other linux distro?

---

### Post by avtolle on 2009-01-29
The Gparted live cd will run the partitioner, and will not try to install any OS.

---

### Post by polskimoose on 2009-01-29
to be honest. i have NO idea what any of this means

whats wrong with wubi?

---

### Post by Pumalite on 2009-01-29
[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)
[http://en.wikipedia.org/wiki/Wubi_(Ubuntu](http://en.wikipedia.org/wiki/Wubi_(Ubuntu))

---

### Post by boof1988 on 2009-01-29
> **polskimoose said:**
> whats the difference between the ubuntu live cd and the gparted cd?

The Ubuntu LiveCD is also known as a Desktop-Installer.   It has a desktop *live environment* that allows (among other things) two features:
[LIST=1]
[*]The option to use the OS without installing to the HDD (the OS loads [EDIT ADD: stuff as needed] to memory).
[*]The option to install the OS (the OS is installed to a HDD/USB etc).
[/LIST]

> **polskimoose said:**
> will it install ubuntu or some other linux distro?

I don't think the GPartEd LiveCD provides any *Install* options.  It loads a Debian OS with basic utilities.  GPartEd is one of the utilities included.  It even provides a "load entirely to RAM" option so that the CD can be removed once the OS is loaded.  This opens up the drive for other uses.

---

