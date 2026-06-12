---
title: "Tablet PC screen swivel event"
date: 2005-12-13
forum: Hardware &amp; Laptops
---

### Post by 23meg on 2005-12-13
As the title should suggest, I'd like to detect the screen swivel event of my tablet pc and assign it to a function, such as a script that automatically rotates the X orientation with xrandr. How can this be accomplished? I'm not seeing any events generated in dmesg, and haven't had any success with evrouter listening to /dev/input events either.

---

### Post by 23meg on 2005-12-20
I tried listening with acpi_listen but it just returns the regular lid open/close events, no lid swiwel event.. any ideas?

---

### Post by Linuturk on 2007-03-07
I don't even know how to monitor those events.

There has to be some sort of hald trigger. Otherwise, Windoze wouldn't auto rotate it's screen.

[http://www.ubuntuforums.org/showthread.php?p=2256368](http://www.ubuntuforums.org/showthread.php?p=2256368)

---

### Post by Linuturk on 2007-09-26
Any luck finding that swivel event 23meg?

---

### Post by 23meg on 2007-09-28
No, but I haven't really checked it out in the last few kernel versions. I'll keep you posted here if I do find something.

---

