---
title: "Problem adding a new HD"
date: 2008-11-15
forum: General Help
---

### Post by QuickFinder on 2008-11-15
My old computer recently died due to overheating in the graphics card. I removed the hard drive, bought a new computer, and installed Ubuntu onto the new computer.

Then I thought I'd add the old hard drive in addition to the exiting one. I plugged it in, and started up the computer. The problem is that nothing appears on my monitor now. I tried removing the old hard drive, and still nothing. I tried a live CD, and still nothing. I don't see a system screen, I don't see "Compaq" appear. The monitor isn't getting anything whatsoever.

The graphics card on the new machine is an nvidia card, so I've had graphics issues before, but I think I should at least be able to see the system screen on booting.

If anyone has any idea what might be wrong, any help would be appreciated at this point.

---

### Post by wolfen69 on 2008-11-15
if you have access to another video card, try that. if that does not work, i'm afraid your motherboard is probably fried. plus, double check all physical connections.

---

### Post by Mardoct909 on 2008-11-15
If you're getting nothing at all at any point, it's either the monitor or - more likely in this case - a broken motherboard as wolfen69 said.

It isn't the hard disk either way. First the mobo starts up, does the POST - power on self test - and if it passes moves on to showing you a splash screen - where it says "press DEL to configure" or some such and sometimes shows a picture in the background with the company name - then moves on to booting up from the master disk.

If there's nothing getting to the monitor at all, that means that there has been a failure before the boot process starts. If the mobo doesn't past the POST then it will give a beep code to you to signify what is wrong.  So that means that the problem is that the mobo is so damaged it can't do the POST at all, or that the it is passing the POST but unable to communicate with the monitor.

Are you still using a graphics card, or integrated graphics?

If you have a card, it could easily be that the card is at fault. If it's integrated, the mobo would have beeped about it being broken.

---

