---
title: "Make Logoff actually reboot?"
date: 2008-10-06
forum: General Help
---

### Post by pertheusual on 2008-10-06
Hello all,
   I would like to remove the ability for users to log off.

Either the button should be removed, or hitting the button should just make the computer reboot. 

Any ideas?

I'd also love if this would also happen when the user does ctrl-alt-backspace.

A little background, if you want. I have a system that uses pam_mount to mount a user's samba directory, but when they log off, it doesn't unmount immediately(takes a minute or 2), so the easiest way I see to avoid this is to just have the system reboot on logout.


Thanks much.

Per

---

### Post by ronnielsen1 on 2008-10-06
This will do the first part

[http://www.cyberciti.biz/faq/linux-unix-remove-gui-shutdown-reboot-option/](http://www.cyberciti.biz/faq/linux-unix-remove-gui-shutdown-reboot-option/)

2nd part
[http://ubuntuforums.org/showthread.php?t=146590](http://ubuntuforums.org/showthread.php?t=146590)

---

