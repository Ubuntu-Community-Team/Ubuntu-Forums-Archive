---
title: "HP DV5000 laptops hard drive light stays on when idle"
date: 2008-11-22
forum: Hardware
---

### Post by Crow550 on 2008-11-22
I posted this in the Beginner area, but I assume this would be closer to the correct area.

Here is the post: 

[http://ubuntuforums.org/showthread.php?t=989730](http://ubuntuforums.org/showthread.php?t=989730)

---

### Post by Crow550 on 2008-11-23
Can anyone help with this?

---

### Post by Crow550 on 2008-11-24
Problem fixed.... Laptop mode wasn't enabled. I just opened the terminal and typed sudo /etc/default/acpi-support then went to search and laptop and found ENABLE_LAPTOP_MODE and set it from false to true. I figured this out after doing some research and decided to check if it was on.

I don't know why Ubuntu didn't figure out it was a laptop in the first place. I also heard when installing Ubuntu to go into other options and select laptop mode? Why can't it detect a laptop or ask you if your installing it on a desktop or laptop?

---

