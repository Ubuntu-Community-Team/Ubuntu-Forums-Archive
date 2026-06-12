---
title: "NVIDIA 270 driver system lock-up"
date: 2011-03-17
forum: Hardware
---

### Post by vinx on 2011-03-17
My system had random lock-ups and I think I found the source of the trouble: NVIDIA's version 270 beta-driver.

This is what happens a few times a day:
[LIST]
[*]Random lock-up starting with 4 or 5 white flashes of the screen
[*]Keyboard mostly not working anymore
[*]Mouse still working
[*]CPU usage increasing (fan blowing)
[*]LOG: 4x "NVRM: Xid (0000:01:00): 13, 0003 00000000 00008297 00001514 00000000 00000040"
[*]LOG: 4x "NVRM: Xid (0000:01:00): 13, 0003 00000000 00008297 00001408 00000001 00000040"
[/LIST]

Just go back to driver version 260.

---

### Post by hokage on 2011-04-17
I can confirm the same behaviour with an NVS 3100M. Reverting to 260 that was fine.

---

### Post by vinx on 2011-05-18
I added a screenshot at [http://ubuntuforums.org/showthread.php?t=1761853](http://ubuntuforums.org/showthread.php?t=1761853) of how the screen can look like when the trouble starts.

---

