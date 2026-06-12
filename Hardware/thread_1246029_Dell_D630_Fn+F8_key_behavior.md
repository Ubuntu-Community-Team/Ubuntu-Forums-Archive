---
title: "Dell D630 Fn+F8 key behavior"
date: 2009-08-21
forum: Hardware
---

### Post by BoBaH32 on 2009-08-21
Hi all,

Fn+F8 keys (CRT/LCD switch) behavior is wrong on dell D630 laptop, ubuntu jaunty 9.04.
I  use xrandr to switch between laptop and external display.
I wanted to remap this key to my script which change the resolution and found a solution in [this thread]("http://ubuntuforums.org/archive/index.php/t-634675.html"). 
But altering /etc/acpi/events/videobtn didn't gave a result because Fn + F8 is handled not only by acpid (after stopping acpid, pressing Fn+F8 still chaged video modes).
I read wiki about [hotkeys architecture]("https://wiki.ubuntu.com/Hotkeys/Architecture") but still haven't idea in what place I can change handler for this key combination.

Any help is welcome.

Thanks in advance.

---

