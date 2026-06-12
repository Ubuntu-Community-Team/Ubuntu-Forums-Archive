---
title: "Please talk to me about dual-booting as if I were a child"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by poubelle on 2009-07-14
Hi all,

I'm a relatively new Ubuntu user, and I use only Ubuntu. But my stepfather, who is visiting, uses a Windows laptop and would like to dual-boot Ubuntu. (A complete switch is pretty unlikely in the near future, because it's a work computer, but not out of the question.)

We installed Ubuntu Jaunty on his laptop through Wubi. It works great and everything (though he's still looking for his photos and MP3s through Ubuntu's file system) but he's concerned about his hard-drive space. I haven't used Windows computers in about 15 years (was a Mac person before switching to Linux) so I don't know much about partitions and such, yet I suspect this has something to do with filesystems and partitions and such. Can someone walk me through this in small words with few syllables?

His hard drive is 75GB. 

With just Windows installed he had 54GB free. 

With Ubuntu installed (via Wubi) he has two numers:
- Ubuntu reports only 13GB free
- Windows reports 35GB free (??)

I understand Wubi installs within the existing Windows partition, and a regular install from the bootable CD asks for new partitions to be created. As I said, I know very little about partitioning, so I don't know how or if this plays into the problem.

A few questions.

1. Why does Ubuntu report the drive to be so full? Which number is definitive: Windows' or Ubuntu's?

2. Windows says that the Ubuntu install took up 19GB... why? On my system it's less than 10GB. 

3. Would uninstalling (via Windows' add/remove programs) and reinstalling (by booting from the CD) help? (Bonus question: if so, why?)


He's really concerned about his hard-drive space (perhaps a teeny bit obsessed with that figure, and doesn't want to run out sooner than necessary) so the disparity in numbers and the hugeness of the Ubuntu install are concerning him, and I think he'll probably remove it. Can anyone talk me through the best options to minimize the amount of hard-drive space taken by Ubuntu?

Thank you! I really want to help someone who's interested in Ubuntu -- I'd hate for him to be turned off altogether -- but my knowledge in Wintel stuff is limited.

---

### Post by Operan on 2009-07-14
Dear poubelle,
When you install Ubuntu via Wubi, the installer would take 20GB( I guess that you select about 20GB to install Ubuntu in Wubi Install Wizard ) of harddrive to make an virtual harddrive / virtual partion to install Ubuntu. So if you are in Windows, it reports that folder "Ubuntu" has a size of 20GB, it is correct!
But Ubuntu has just used only less than 10GB of that "virtual hard drive", and it reports that 13GB is free (of 20GB ), it's also correct :))

Windows really doesn't know how much capacity Ubuntu uses.

Hope you understand!

---

