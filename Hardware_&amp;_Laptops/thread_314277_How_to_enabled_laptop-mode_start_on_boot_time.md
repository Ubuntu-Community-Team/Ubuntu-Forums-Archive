---
title: "How to enabled laptop-mode start on boot time?"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by EDzior on 2006-12-07
Hi. I've done all configuration in /etc/default/acpi-support and /etc/laptop-mode/laptop-mode.conf as it sais here: 
[http://ubuntuforums.org/showthread.php?t=305693&highlight=laptop-mode]("http://ubuntuforums.org/showthread.php?t=305693&highlight=laptop-mode")
The problem is that laptop-mode script is not starting at boot time, i must start him manually. I did chmod +x to make him executable but it didn't change anything. What do i need to do to make laptop-mode start on boot-time?
Sorry for my english and thanks for any help.

---

### Post by EDzior on 2006-12-07
Ok. Problem solved. This was easy in fact. I did:
**[B]sudo update-rc.d laptop-mode multiuser**[/B]
and now laptop-mode is starting on system boot.

---

