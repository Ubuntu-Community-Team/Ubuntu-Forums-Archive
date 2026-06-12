---
title: "Compiz not working with Intrepid Ibex"
date: 2008-11-01
forum: General Help
---

### Post by omnibot on 2008-11-01
Compiz is installed and the manager comes up but the effects are not running. 

I tried searching and for most people the problem was with an nvidia card but I have an intel video card. 
It was working fine with Hardy. 

When I open terminal and type in "compiz" i lose my window borders and have to reboot to get them working. 

any idea?

---

### Post by PC_load_letter on 2008-11-01
Sorry, didn't read your question in full. 
I'm no expert, but it looks like a driver issue.

---

### Post by omnibot on 2008-11-01
also my AWN isn't working. Maybe they have a common root problem?

---

### Post by omnibot on 2008-11-01
> **PC_load_letter said:**
> Sorry, didn't read your question in full. 
I'm no expert, but it looks like a driver issue.

it's an intel G965 

is there a terminal command to update drivers?

---

### Post by Cl0ud9 on 2008-11-01
> **omnibot said:**
> it's an intel G965 

is there a terminal command to update drivers?


You can use envyng to update the drivers.
Compiz wasn't working for me either after upgrading, but for some reason using the command line and typing "compiz --replace" made things work for me.

---

### Post by omnibot on 2008-11-01
Fixed. 

i'm not sure if it was one or the other but I installed the ati driver with envyng and then also went into the recovery boot in GRUB and did the "fix broken packages" and went i logged back in, everything worked. yay

---

