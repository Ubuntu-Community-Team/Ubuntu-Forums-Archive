---
title: "Brightness Issue on Samsung Laptop"
date: 2012-08-20
forum: Hardware
---

### Post by porky101 on 2012-08-20
I have a Samsung QX411-W02UB laptop and I have tried installing Ubuntu 12.04-64bit from the ISO file and from WUBI and I am getting the same issue.  Right after I install it the OS works fine, then after a reboot the issue occurs.  Once I reboot and login the OS runs fine for a couple minutes, then the brightness notification bubble pops up (automatically) and the screen flickers and the OS freezes.  

Anyone else having the issue, or know what it is?  I was going to try a install of an earlier version of Ubuntu, either 11.04 or 11.10 a little later today to see what happens.

---

### Post by 2F4U on 2012-08-20
What are the hardware specs, what graphics card do you have? In case of ATI or nVidia, did you install the proprietary graphics drivers? Did you look into the system log file whether it contains hints on why the machine freezes?

---

### Post by porky101 on 2012-08-20
It is an intel graphics card, i did a fresh install of 12.04 from ISO yesterday and installed the first 300 updates it had, then rebooted and shutdown, a little bit later in the day I turned it back on and got the issue...i dont think i have enough time to get to the system log and look at it before it freezes again...only get a couple of minutes

---

### Post by qechappell on 2012-08-20
I have the same problem on my samsung.  When I first installed ubuntu, it worked fine.  Then I updated it and started having the exact same problem. I'm very new to ubuntu and linux in general so I haven't figured out a fix yet. My temporary workaround has been to boot with a previous kernel.  Hold shift while booting and select "boot using previous kernel"(or something like that), 3.2.0-23 works for me. You have to do it everytime you boot though, but it works.

---

