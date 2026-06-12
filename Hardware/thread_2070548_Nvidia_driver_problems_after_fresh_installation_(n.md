---
title: "Nvidia driver problems after fresh installation (newbie)"
date: 2012-10-13
forum: Hardware
---

### Post by hariskar on 2012-10-13
I installed Kubuntu today and had this problem:
Dual boot launched, it asked for login and pass, I gave it and it stops at a black command line screen that has my computer name
hk@hkP5K-WM:~$
I types startx and it says: FATAL: Error inserting nvidia_173 (...): No such device

I then booted with nomodeset but although it booted normally, when I clicked with my Microsoft mouse there was nothing happening. I see the cursor moving but most of the times no result on clicking and hovering. Also, right click does not work neither keyboard shortcuts. Are these mouse and keyborard problems or they are connected with nvidia problem?
With Live CD there is no problem with all above.
What can I do?
Thank you

---

### Post by hydn79 on 2012-10-13
I think this is a bug:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/522328](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/522328)

---

### Post by hariskar on 2012-10-13
Thank you. Is it fixed in 12.10 beta? Could I do something from command line? KDE opens but it is not functional..
This bug is from year 2010. Is it still not fixed?
Why does this problem not exist in Live CD?

---

### Post by hariskar on 2012-10-15
I installed kubuntu 12.10 beta with the problem remaining.
BUT: ubuntu, debian, fedora, mint work without problems...

---

