---
title: "Mouse lag and freeze in Ubuntu 17.10 Wayland"
date: 2017-10-30
forum: Hardware
---

### Post by munichmachine59 on 2017-10-30
Hi

I have a USB 2.0 mouse which freezes up sometimes when I leave it for typing. Is there a setting I can set? Because its fine in X server.

---

### Post by calfax on 2018-01-20
This happened to me when I decided to upgrade Ubuntu 17.04 to 17.10 due to EOL for 17.04.  After the upgrade, my USB mouse was horribly laggy on both Wayland and Xorg with both Unity and Gnome (and Cinnamon).  In my opinion, this is entirely unacceptable: in 2018, mice and other peripherals (and printers) should "just work", especially if they are simple USB peripherals.  Of mention, I am running Nvidia proprietary drivers, but when in software rendered Cinnamon DE, I also experienced mouse lag as well.  

So:

1. Logging out of Unity DE (and Gnome on Wayland) and into an Xorg DE did not resolve the problem - the mouse was still laggy.

2.  Edit /etc/default/grub :

     GRUB_CMDLINE_LINUX_DEFAULT="quiet splash irqpoll"

failed as well.

3.  Edit /etc/default/grub:

    GRUB_CMDLINE_LINUX_DEFAULT="acpi_rev_overrride=1" 

failed as well.

4.  What has finally worked was 

adding

-r usbhid
usbhid mousepoll=1

to /etc/modules and rebooting.

I hope this helps someone else.

---

