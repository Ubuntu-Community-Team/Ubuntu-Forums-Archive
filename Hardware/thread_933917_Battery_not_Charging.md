---
title: "Battery not Charging?"
date: 2008-09-29
forum: Hardware
---

### Post by syntaxing on 2008-09-29
I tried searching the forum but i haven't seen a post like this, but i probably overlooked. But the problem I have is that the batter is not charging when I am in Ubuntu. I first ran Xubuntu and everything was fine but when I installed Ubuntu the battery indicator says that its charging then...not. I have a battery indicator light that tells me if my battery is charged on the the laptop itself. When I am in ubuntu the light turns on for 5 secs or so then turns off. The weird thing is when I turn off my computer the battery charges. I even let my laptop run until the battery dies and the moment it dies, the battery charging indicator goes on at the same time. I was wondering if this is my problem or is this a known bug?

---

### Post by alohadiaz on 2008-09-29
I also am having similar issues. I am new so cant help you but I am extremely interested as to what comments the more experienced users might have. My battery charges it just doesn't las as long as it would if i was using vista.

---

### Post by BadgerKid on 2008-12-03
I ran into this with ubuntu amd64 8.04.1. I discovered it while playing around with cpu frequency scaling. The battery was down to 24% and wouldn't increase. The recharging light on the battery was not lit, so somehow power wasn't being let into the battery.

At some point after removing the 'noapic' option from the kernel boot line in /boot/grub/menu.lst, the battery starting on its own again.

---

### Post by BadgerKid on 2008-12-04
I think I have a possible solution.  With the AC power running, remove the battery and wait until the battery monitor shows 0%. Then reinstall the battery.  Linux will detect the battery and show the previous charge level, but voila! the battery will now start charging :D

 (Notes: I discovered this solution after having done the upgrade (sic) from Hardy to Ibex with the hope, based on what I read on the 'net, that the newer kernel version had improved apci functionality.  The battery issue isn't fixed in ibex for me however.)

---

