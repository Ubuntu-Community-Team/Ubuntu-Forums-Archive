---
title: "Ubuntu 11.04 wastes memory only when its available?"
date: 2011-09-03
forum: Hardware
---

### Post by Coder543 on 2011-09-03
I have noticed this.. on my Ubuntu 11.04 machine with 8GB RAM and 64 bit, it uses 800 to 1200 mb RAM just for the OS and nVidia driver at a clean desktop. Whereas on an older machine with only 1GB RAM and also 64 bit, with nVidia, it only uses about 450mb. On a laptop sans nVidia and running 32 bit, it uses only like 300mb.

What is the deal?

---

### Post by .... on 2011-09-03
If more memory is available, the virtual memory manager will be more liberal with keeping old data/instructions in the main memory instead of swapping them out or removing them from the cache. This is a good thing for performance as that data is available in the cache should you need it again. If you suddenly ran a bunch of programs that needed RAM and started running out, then the virtual memory manager would swap or remove currently unused data.

Note: 64-bit tends to use a bit more RAM because the data pointers are, well, 64 bits (instead of 32).

---

### Post by Coder543 on 2011-09-03
No, I thought of that, but the 1gb + nvidia machine does not even have a swap space as of late.. even though that can cause the computer to run out of memory and lock up on occasion. Its not swapping to disk, its just being more efficient.. that's what I don't understand.

---

### Post by Coder543 on 2011-09-05
bump?

---

