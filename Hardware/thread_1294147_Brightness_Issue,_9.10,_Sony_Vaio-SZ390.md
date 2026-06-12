---
title: "Brightness Issue, 9.10, Sony Vaio-SZ390"
date: 2009-10-17
forum: Hardware
---

### Post by rosiny on 2009-10-17
I realize this is probably a popular complaint, but my brightness keys don't work. 

I wouldn't be that bothered by this, but a bigger issue is that xbacklight returns the following output, not changing the brightness, leaving me with the issue that I can't use my laptop without wearing sunglasses (if you guys have sony vaio's you should know why - the brightness goes up obscenely high). 

```
No outputs have backlight property
```

I've attempted looking into /etc/apci/, but the only apparent brightness files are "asus-brn-down.sh" and "asus-brn-up.sh," which I suspect is my problem, since this is a vaio...

In any case, does anyone have any suggestions? The asus files only have the following in the file:

```

#!/bin/sh

test -f /usr/share/acpi-support/key-constants || exit 0
. /usr/share/acpi-support/key-constants
acpi_fakekey $KEY_BRIGHTNESSDOWN

```

---

### Post by rosiny on 2009-10-18
Any ideas? =/

---

### Post by rosiny on 2009-10-19
Hm. Or... is there any way to change the brightness buttons so they read a different file, other than the asus-brn-up and down files?

---

### Post by Nalroff on 2009-10-19
Have you tried firing the brightness down event manually? You should be able to find the code under /dev/input/event#. You'll have to hunt for the right code, but when you find it you can fire the event using
```

sudo acpi_fakekey KEYCODE

```
Let us know if it works.

---

### Post by Nalroff on 2009-10-19
My bad. Should have looked at your post a bit closer. This won't help you. Sorry.

---

### Post by rosiny on 2009-10-21
Thanks, anyways. Does anyone have any other suggestions? I can't keep wearing sunglasses when using my computer. =( This is especially a problem during class. =(

---

### Post by rosiny on 2009-10-25
Problem still not fixed. Any ideas?

---

### Post by rosiny on 2009-10-26
So I decided to just suck it up, and found a temporary solution -

```
sudo nvclock -S 15
```

Sadly, I'm certain my computer can be much less bright as well, but nvclock won't let me go below 15. =/ 

Please let me know if you have any other suggestions. Thanks!

---

### Post by liangbin1978 on 2009-11-30
You can refer to [http://ubuntuforums.org/showthread.php?t=1156337](http://ubuntuforums.org/showthread.php?t=1156337).

---

