---
title: "Small problem with dmraid and initramfs"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by nyteshade on 2009-04-28
I am sooo close to getting my system working properly. My machine is a 4GB M3N-HT mobo running a 1.5TB spanned nvidia sata raid. The install is Jaunty 9.04.

The machine currently boots and then fails into an initramfs shell. To get it booting I type the following

(initramfs) dmraid -ay
(initramfs) exit

Then the machine continues booting. I have tried unpacking the init image, and modifying the init script to call dmraid -ay and repacking the init image and I can see my changes but they do not solve the problem.

Can someone help me fix the system such that I don't have to drop into the initramfs shell anymore?

And please if the ubuntu gods are listening (support dmraid from the get to in the gui installer). NONE of my friends would have been able to get even this far if they wanted to install it on their nvidia raid machines.

---

