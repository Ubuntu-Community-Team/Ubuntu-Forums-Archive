---
title: "Add/Remove applications problem"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by Nilafhiosagam on 2009-10-01
Hi,

I'm new to Ubuntu and have heard good things so I decided to try it out on my 2nd computer. All was going pretty well until about an hour ago. I installed a couple of programs via the Add/Remove applications program but it now gives me an error message when I attempt to install something. For example when I try to install Amarok I recieve the following message:

"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

What exactly does this mean and how can I get around it?

Thanks

Edit: And it seems I posted this in the wrong forum. Maybe a Mod could move it for me?

---

### Post by mharrison on 2009-10-01
> **Nilafhiosagam said:**
> Hi,

I'm new to Ubuntu and have heard good things so I decided to try it out on my 2nd computer. All was going pretty well until about an hour ago. I installed a couple of programs via the Add/Remove applications program but it now gives me an error message when I attempt to install something. For example when I try to install Amarok I recieve the following message:

"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

What exactly does this mean and how can I get around it?

Thanks

Not an expert or high level novice, but if it is telling you to run something to correct a problem, I would suggest running the command it is telling you to run and see if that resolves your problem.

---

### Post by wojox on 2009-10-01
Open the terminal and run:

```
sudo dpkg --configure -a
```

---

### Post by Nilafhiosagam on 2009-10-01
Ah thanks.

Like I said I'm new to Ubuntu. I had no idea it was that simple!

---

### Post by satishbhawra42 on 2009-10-01
Nice information thanks for the discussion

---

