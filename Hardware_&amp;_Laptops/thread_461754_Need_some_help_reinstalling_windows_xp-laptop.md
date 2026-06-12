---
title: "Need some help reinstalling windows xp-laptop"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by goddannor on 2007-06-02
Issue fixed.

---

### Post by coffeecat on 2007-06-02
I only have experience of installing XP on a blank drive so what I say may be entirely unhelpful, but here goes anyway.

Unlike Linux, Windows **must** be on a primary partition, and the partition must be marked with the boot flag. In my Windows partitioner there is something about an 'active' flag. To be honest, I'm not quite sure what this is because I've never found a need for it in Linux. :)

I suggest you have a look in gparted again and make sure you're setting up a primary partition with the boot/active/whichever flag. Perhaps, if you're wanting to ditch Linux on that machine, it would be a good idea to completely reformat the whole disk because it's possible that the Windows install disk is being thrown by the partition table. Also, make sure you've got a disklabel set under Device > Disklabel in Gparted.

**Edit:** You wiped your whole post and replaced with 'issue fixed' at the same time as I posted. Be aware that others read these threads for help. If my suggestion was correct, please post again or re-edit your original post. It may be helpful to others.

---

### Post by coffeecat on 2007-07-17
Potbo :(

---

