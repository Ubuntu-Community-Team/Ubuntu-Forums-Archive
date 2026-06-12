---
title: "Laptop: automatic wakeup after suspend"
date: 2014-09-09
forum: Hardware
---

### Post by rbaum on 2014-09-09
Hello all,

I hope somebody can help me to develop a solution to the following problem I have with my Macbook Air 6-2/Ubuntu 13.10:

When I close the lid of my laptop, the the system is going into sleep (suspend-to-ram) mode as supposed to to. But after 3-6 seconds it wakes up again.
I've to open and close the lid again to initiate a new "go to sleep" event. After doing so, the laptop stays in suspend mode.

I cannot find any clues in the log file why my system wakes up again, but i can see that the 1st suspend mode is reached completely (CPUs go offline) and after this, it wakes up again.
This behaviour is somewhat suspicious, because after a fresh reboot the system stays in sleep mode by the first try. Just after using it several hours, the described "wake-up-again"-behaviour occours.

There is no additional hardware attached or special applications running in any situation that could cause the described behaviour.

Does anybody has an idea how to debug this problem or how to get a solution for this?


Thanks in advance

r.

---

