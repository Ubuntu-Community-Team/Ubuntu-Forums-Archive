---
title: "[SOLVED] System VERY SLOW at times, Fast at others?"
date: 2008-08-25
forum: General Help
---

### Post by ddarsow on 2008-08-25
I have a Dell Latitude D620 with 2GB of RAM and an Intel Centrino Duo 1.83GHz processor. Ubuntu 8.04.01 Hardy LTS is installed as the only OS (it is NOT a dual boot machine).

Most of the time the machine runs blazingly fast and is highly superior to when it was a Windows box. However, it occasionally gets VERY SLOW. It gets to the point of having as much as a 30 second delay before anything happens. 

I am running Compiz and turning it off does NOT change anything. The problem usually shows up after viewing large .pdf files although this is not always the case.

It also seems to happen more when connected to our network at the law school via VPN. It almost never happens at home.

Is there some way to tell what is bogging it down when this happens? I suspect that it may be heat related as even rebooting will not fix the problem sometimes. However, it is not noticeably hotter (to touch anyway_ when it happens.)

Basically I am needing to know where to begin to look for the source of the problem. The CPU (both threads) will usually be in the high 80% when it happens and I also notice that the swap file is in use (seems odd with the amount of RAM I have).

Multi-tasking does not seem to trigger it and even when running multiple apps such as: Gimp, Writer, Amarok, and several instances of Firefox does not cause the use of system resources as when the problem occurs.

---

### Post by sdennie on 2008-08-25
If you are seeing swap usage with 2GB of RAM, something odd is happening.  The next time you notice the machine behaving oddly, bring up a terminal and type "top".  From there, you can sort processes by RAM usage by hitting "F", "n", Enter.  My guess is that it will be fairly obvious what is happening after that.

---

### Post by mssever on 2008-08-25
It might also pay to run memtest86 overnight to check your RAM.

---

### Post by ddarsow on 2008-08-26
My machine ran flawlessly last night at home. This morning, back at the law school connected to VPN (not sure if relevant), it began running VERY slow again.

Executing top shows that Xorg is using 97% of CPU resources.

As an indication of how slow I am running, it took me about 4 minutes to be able to reply to this thread from the time I cliucked on the link to it. That would normally be about a 2 second thing.

[SOLVED]:

It turns out it was a temp problem as I initially suspected. After enabling powernowd to throttle the processor speed and installing Gkrellm to manage the fan speed the problem has gone away.

My temp was climbing as high as 79c before as the processor was running full bore at all times and the fan stayed on low.

---

