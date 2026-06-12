---
title: "On battery (run a script)"
date: 2007-03-05
forum: Hardware &amp; Laptops
---

### Post by patrickclover on 2007-03-05
Hi I was wondering if when i unplugged my laptop i could make it run a small script? like this:

echo "1" > /proc/acpi/sony/brightness

Thanks this would make my day if you know how to do this :) 

/Patrick Clover

---

### Post by brettr on 2007-03-05
If you have laptop-mode enabled, i believe you can put one in "/etc/laptop-mode/batt-start/" and "/etc/laptop-mode/batt-stop"

But you need to make sure laptop-mode is enabled

---

### Post by patrickclover on 2007-03-05
Ok thanks, so how do i add:

echo "1" > /proc/acpi/sony/brightness

??? and get it to work?

---

### Post by brettr on 2007-03-12
Well, check out this post for info on how to enable laptop-mode [Ipw2200 power management]("http://ubuntuforums.org/showthread.php?t=339089") After that you probably would need to create a little shell script.

First you create the file
```
 sudo gedit /etc/laptop-mode/batt-start/20-brightness.sh
```

then put something like this in that file
```

#!/bin/bash
echo "1" > /proc/acpi/sony/brightness

```

Just a note though i am not sure about that 20 at the beginning of the filename, i am not sure if you need to have a different number or not... I can't try it, i don't have this "/proc/acpi/sony/brightness" file. Hope that was somewhat helpful

---

