---
title: "Suspend behaving stupidly on Thinkpad"
date: 2011-02-01
forum: Hardware
---

### Post by aard on 2011-02-01
Hello everyone.

I'm having trouble putting my Thinkpad R500 into sleep/suspend mode. It's been behaving erratically since 10.10 came out (both an upgrade from 10.04 and a fresh install that I did in attempt to solve the issues).
Kernels up to 2.6.35-25-generic sometimes hang with a blank screen with an underscore in the top left corner when I try to suspend the machine (the sleep LED on the machine blinks). This happens about 50% of sleep attempts, and the machine just stays like that until I power it down or it runs out of battery. Sometimes, instead of the blank screen, it freezes with "Starting VirtualBox kernel modules" (tho, sometimes it doesn't freeze but enter sleep normally)
Kernel 2.6.35-25-generic just wakes up from sleep instantly the moment I click suspend or lower the lid of the notebook.

What do I do? I have no idea what's causing this. Should I just nuke the install once again and migrate back to 10.04?

---

### Post by ivoks on 2011-02-02
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/705845](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/705845)

---

### Post by aard on 2011-02-07
> **ivoks said:**
> [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/705845](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/705845)

Zahvaljujem! :)

Solves the issue :)

---

