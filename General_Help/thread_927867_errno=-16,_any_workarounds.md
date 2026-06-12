---
title: "errno=-16, any workarounds?"
date: 2008-09-23
forum: General Help
---

### Post by SpinningAround on 2008-09-23
I get errno=-16 and wonder if there is any workarounds? I think the problem occur when you got a motherboard that only support 150mb/s sata while you got a harddrive with 300mb/s.

---

### Post by Atsuko on 2008-09-23
Does it happen when it is doing the partition work.

---

### Post by northern lights on 2008-09-23
Try to reinstall GRUB.


1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
...

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, restart your computer

---

