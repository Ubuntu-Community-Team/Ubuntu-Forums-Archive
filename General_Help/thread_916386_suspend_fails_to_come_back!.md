---
title: "suspend fails to come back!"
date: 2008-09-10
forum: General Help
---

### Post by compu73rg33k on 2008-09-10
If I suspend the system when I come to wake the computer back up, the lights all come back on, but the screen is black. I try to switch to tty1 but nothing happens and I have to push alt + SysRq + b to reboot. It's hard to debug this because the problem ends in me having to restart the computer.

lspci is attached

---

### Post by Lord Xeb on 2008-09-10
same here. It has something to do with ACPI

---

### Post by compu73rg33k on 2008-09-10
Is there any sort of possible fix you've heard of?

---

### Post by compu73rg33k on 2008-09-12
If I restart x-server, it comes back on. (ctrl+atl+backspace)

---

### Post by unutbu on 2008-09-24
Have you found a solution to this problem compu73rg33k?

If not, here is a similar thread where the black screen after suspend was solved by disabling ehci_hcd: 

See [http://ubuntuforums.org/showthread.php?t=817300](http://ubuntuforums.org/showthread.php?t=817300) and 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/243967](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/243967)
Look at the ends of each of these threads.

---

