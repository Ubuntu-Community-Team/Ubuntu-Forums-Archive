---
title: "no consoles"
date: 2008-11-23
forum: General Help
---

### Post by sunfish on 2008-11-23
Why don't I get any consoles with Ctl-Alt-F1 thru F6? If I send ctl-alt-f2 in an x-terminal I get ";7Q".

I have checked ps aux and I see...

root      4687  0.0  0.0   1716   508 tty4     Ss+  20:27   0:00 /sbin/getty 384
root      4688  0.0  0.0   1716   508 tty5     Ss+  20:27   0:00 /sbin/getty 384
root      4690  0.0  0.0   1716   508 tty2     Ss+  20:27   0:00 /sbin/getty 384
root      4693  0.0  0.0   1716   508 tty3     Ss+  20:27   0:00 /sbin/getty 384
root      4694  0.0  0.0   1716   512 tty6     Ss+  20:27   0:00 /sbin/getty 384

There is no /etc/inittab in Hardy so there is nothing to see there. I really don't know how to check out Upstart to see if things are configured correctly there.:confused:

---

