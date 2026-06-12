---
title: "xubuntu freezes on screensaver"
date: 2011-10-05
forum: Hardware
---

### Post by kokomodrums on 2011-10-05
Computer: Gateway CX2620 (Tablet Screen)
OS: Single Partition - Xubuntu 10.10


So this is a pretty fresh install, and had the same problem on my other Gateway. The whole computer freezes when the screen saver runs for more than a couple minutes. Any ideas???

Thanks!

- Matt

P.S. I've also been having bad luck in general with xubuntu, not sure why cause ubuntu ran fine. Recently, my computer will occasionally run very very slow to the point that i have to turn it off or it will freeze, and it does it right from startup. Other times it loads just fine.

---

### Post by mörgæs on 2011-10-05
When the computer freezes, do you get any kind of error message?

If you run **top** in the background while it is slow, do you see any program eating a lot of CPU cycles?

---

### Post by kokomodrums on 2011-10-06
There is never an error message. How do I run top?

Thanks for the reply!


UPDATE: My clock and dropdown menu has disappeared from my top panel mysteriously...

---

### Post by mörgæs on 2011-10-07
**Top** is a command you run from the terminal (command line). It will show which applications are heavy on the system. Press q for quitting top.

Is the computer stable, if you disable the screen saver and let it stand for several hours?

---

### Post by kokomodrums on 2011-10-20
Update:

Upgraded to Xubuntu 11.04. I added the System Load Monitor and CPU Graph to my top panel. After my computer has ran for 10 minutes or so, the memory gets stuck at 476 of 1000mb. It may fluctuate by 5-10mb, but generally stays there. The CPU is actually running lower on average than when I was running xubuntu 10.10. Not sure what that's about, but I'm not complaining!

It didn't seem to be any specific process that spiked, basically any program I open would take the cpu graph all the way full, and stay there. Like I said though, the CPU seems to be running lower since the upgrade.

The memory is my concern. Oh, and I'm currently running chrome and firefox only. Just regular browsing. So the memory shouldn't be THAT high, I don't think...

---

### Post by mörgæs on 2011-10-20
> **kokomodrums said:**
> 
The memory is my concern. Oh, and I'm currently running chrome and firefox only. Just regular browsing. So the memory shouldn't be THAT high, I don't think...

Why do you ask a question, if you don't pay attention to the answer? I have already told that **top** will give you the overview.

---

