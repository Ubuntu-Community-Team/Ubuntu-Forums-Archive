---
title: "How can I &quot;modify&quot; my mouse position by not using the mouse?"
date: 2010-04-12
forum: Hardware
---

### Post by Mega-X on 2010-04-12
As the topic title, how can I modify my mouse position (Meaning, the cursor) without using the mouse?

I can easily read the input of the mouse by using ```
cat /dev/input/by-id/<nameofthemouse> | hexdump -C
```, but I really can't find out how to change the mouse position; will somebody help me? :confused:

---

### Post by sisco311 on 2010-04-12
System -> Preferences -> Keyboard -> Mouse Keys

or:
```
xdotool mousemove X Y
```
where X & Y are the coordinates.

---

