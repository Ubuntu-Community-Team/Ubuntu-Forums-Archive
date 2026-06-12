---
title: "I can't use dual monitor in a ATI RV740 PRO [Radeon HD 4770] after upgrading"
date: 2014-06-03
forum: Hardware
---

### Post by ianjmorse on 2014-06-03
I had a two monitor set-up on 12.10 and I just upgraded to 13.10 and then 14.04.

As soon as I upgraded to 14.04 my system would continually restart, and would not load the OS. I tried unplugging my second monitor and the system worked fine.

When I plugged in my second monitor again, my system rebooted, and I got the error message 

```
A hyper transport sync flood error occurred on last boot.
```

I ran ```
lspci | grep VGA
``` and got:    

    ```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV740 PRO [Radeon HD 4770]
```

The system would not load again until I unplugged my second monitor. I would like to be able to use both monitors without upgrading my graphics card. Can anyone please advise?

---

### Post by keith-finnie on 2014-10-15
I have a similar problem, using the same video card under Ubuntu 14.04. The problem appeared about a week after beginning to use the second monitor. Two days ago the following behaviours began. 

With two monitors plugged in, about 7 times in 10 my system freezes either shortly before, or shortly after the desktop graphical display appears. The other three, it freezes when recovering from suspend mode, or just after sitting for a while.

The behaviours disappear when the second monitor is unplugged.

---

