---
title: "CPU usage and RAM usage?"
date: 2013-09-01
forum: Hardware
---

### Post by toady2 on 2013-09-01
Does CPU usage affect RAM usage and vice versa? I can't really test CPU usage mainly because I don't have cpu intensive application and my current cpu wouldn't even be able to handle it.

---

### Post by bkline on 2013-09-01
Processor and memory usage are mostly independent of each other.  The exception would be that if memory usage gets so high that the operating system has to swap portions of memory to disk because the running programs have requested more memory than is physically available, additional processing will take place in order to manage that swapping.  That won't show up as a higher CPU usage, though, because the delays introduced by the work to move information from memory to disk and back will interrupt the rest of the work the processors were handling.  In other words, the number of processing cycles to accomplish a given amount of work will increase, but the percentage of the available processing capacity in use at a given moment will go down.

To view CPU usage, you can open a terminal window and run the "top" command, which will show you a load average, as well as the CPU used for each running program.

Hope this helps.

---

