---
title: "Wubi can't complete installation after reboot"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by field33P on 2009-03-13
I've used Wubi for installation of Ubuntu, in Windows all goes fine, but after rebooting into Ubuntu it asks for the timezone (I select GMT+1). That all goes fine, but at the part partition editor it doesn't show any partitions, and clicking Next gives an error (as I must set an partition that won't show up). If I click Cancel, Ubuntu works like an live-cd.

---

### Post by ago on 2009-03-13
> **field33P said:**
> I've used Wubi for installation of Ubuntu, in Windows all goes fine, but after rebooting into Ubuntu it asks for the timezone (I select GMT+1). That all goes fine, but at the part partition editor it doesn't show any partitions, and clicking Next gives an error (as I must set an partition that won't show up). If I click Cancel, Ubuntu works like an live-cd.

Uninstall and reinstall, when you reboot, press ESC quickly after you select "Ubuntu", you will get more boot options. Select verbose mode. If it fails you should have a log in /var/log/syslog which will provide further information (use ctrl+alt+f2 to obtain a console).

---

### Post by field33P on 2009-03-13
> **ago said:**
> Uninstall and reinstall, when you reboot, press ESC quickly after you select "Ubuntu", you will get more boot options. Select verbose mode. If it fails you should have a log in /var/log/syslog which will provide further information (use ctrl+alt+f2 to obtain a console).

Ok, I will try ;-)

---

### Post by field33P on 2009-03-13
Problem has been fixed ;) I´m now running Ubuntu 8.10. Thanks.

---

