---
title: "splash screen splash screen"
date: 2008-10-17
forum: Hardware
---

### Post by wcwashington on 2008-10-17
someone was telling me to do a nosplash on the kernel or something along those lines because the splash screen just stays in one spot after a while and just sits there... he was telling me to do a no splash so i can troubleshoot the problem where do i do this at???? 

i used wubu to install ubuntu because i was having a problem resizing an ntfs partition under win xp and dont have the 80 bucks to shell out for partition magic...

---

### Post by Bucky Ball on 2008-10-17
When you get to the grub menu at boot, choose the kernel you are wanting (don't hit enter!), hit 'e' to edit it, go to the 'kernel' line and add 'nosplash' at the end of that. Hit return then 'b' to boot and see how you go.

---

### Post by wcwashington on 2008-10-17
> **Bucky Ball said:**
> When you get to the grub menu at boot, choose the kernel you are wanting (don't hit enter!), hit 'e' to edit it, go to the 'kernel' line and add 'nosplash' at the end of that. Hit return then 'b' to boot and see how you go.

thanks for the quick response im not a total nub to pc's or at least playing with linux i figured i would do that thanks for the quick response time bucky ball i appreciate it..!!

---

