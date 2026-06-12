---
title: "Ubuntu HANG, $INIT_HALT"
date: 2015-08-08
forum: Hardware
---

### Post by mogio on 2015-08-08
Hi, since 12.04 my pc is haning during shutdown process. System Halt does not switch energy off. I used to solve with noacpi param but after a HD upgrade (from raid 0 to samsung 850 evo ssd) the system didn't boot at all so I tried a lot of solutions. This one is the only one I managed to work: changed  /etc/init.d/halt```
 if [ &#8220;$INIT_HALT&#8221; = &#8220;POWEROFF&#8221; ] && [ -x /etc/init.d/ups-monitor ]
```with```
if [ &#8220;$INIT_HALT&#8221; = &#8220;POWEROFF&#8221; ] -a [ -x /etc/init.d/ups-monitor ]
``` as written in this old (closed) thread: [http://ubuntuforums.org/showthread.php?t=978455&page=3]("http://ubuntuforums.org/showthread.php?t=978455&page=3")

This workaround seems to work but i would like to know if it safe for my hardware.

Thanks.

edit. no, this solution is not working :|

---

