---
title: "/etc/default/acpi-support deprecated?"
date: 2008-05-21
forum: Hardware
---

### Post by Curtisc on 2008-05-21
I've had trouble hibernating ever since I installed Hardy, even though it used to work in Gutsy.  I tried changing all sorts of things in /etc/default/acpi-support to no avail.  Then, I noticed that even though I had specified "HIBERNATE_MODE = shutdown", dmesg was telling me that it was set to "platform".  From the advice on [ this ](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226069) bug report, I changed the hardcoded "platform" in /usr/lib/pm-utils/functions to "shutdown", et voila, hibernation works!

I'm bringing this up here because I notice a lot of support posts about hibernation/suspend issues still say to edit options in /etc/default/acpi-support.  Does this file ever get touched, or has it been replaced by a different configuration system?

---

