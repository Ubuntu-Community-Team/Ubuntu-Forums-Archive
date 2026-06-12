---
title: "Install always freezes at;  Installing System 82% scanning the mirror"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by ozguitarplayer on 2009-02-28
Hi,

I have a 500Gb hdd split 50/50 with 8.10 and 8.04 systems.

Wanted to do some partitioning and used GPartEd, all went well, or so I thought.

On the next reboot I had a grub error 5, I think was.

For various reasons I figures that a complete reinstall and partition would be best.

The issue is that now when I try to install either Kubuntu 8.10,
Ubuntu 8.10 or Hardy Heron 8.04 the install gets to the ....Installing System - Configure Apt...stage the install locks up it's at 82% of install, locks up and that's it, no go.

I have Windows on a sepetate hdd and have been able to delete the partitions on the Linux hdd and have only unallocated space
left, so I used this to make sure I had a clean hdd to work with.
Same result always...locks up at 82% fo install.

Surely three Live CD's can't have all gone bad at the same time?
So if the problem somewhere in the hdd?

Where, what else could the problem be?

Help! I'm living in Windows again till I can fix this....

---

### Post by Partyboi2 on 2009-02-28
Try disconnecting from the Internet before you start the install.

---

### Post by ozguitarplayer on 2009-02-28
unreal...thanks heaps Partyboi2..that worked, but if I may ask....I know I've done installs before while connected to the internet, so why would it make a difference this time?
and how is Jaunty Jackalope?
Thanks again I'm much relieved

---

### Post by Neo_The_User on 2009-02-28
Right when it reaches 80% (not 82%) hit Control Alt F1 or F2 or F3 or F4 and see why it hangs / breaks / or freezes.

---

