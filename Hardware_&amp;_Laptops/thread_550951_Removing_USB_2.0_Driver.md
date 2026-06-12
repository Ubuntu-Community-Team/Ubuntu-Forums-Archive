---
title: "Removing USB 2.0 Driver"
date: 2007-09-14
forum: Hardware &amp; Laptops
---

### Post by snakeminidez on 2007-09-14
Does anyone know how to remove USB 2.0 driver from Linux. There was one site that said to: "do it from the console: *sudo rmmod ehci_hcd*" but I have know clue what or where this "console" is or if he actually meant Terminal. And I did try it in console and I don't think it worked.

---

### Post by eggdeng on 2007-09-14
Console does mean the same as  terminal. If you didn't get an error message, the command executed successfully - you can check by typing  lsmod | grep ehci_hcd in a terminal. No output means it is not loading.

---

