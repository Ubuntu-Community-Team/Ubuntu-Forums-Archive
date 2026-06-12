---
title: "System start problem......"
date: 2008-07-24
forum: General Help
---

### Post by Rodhill on 2008-07-24
I was using Ubuntu 8.04 this morning ok. I installed some updates and got the icon to re-start the PC. When I did this it goes through the post boot ok and then I get a black screen with the words 'System starting' and then it just hangs - anyone can help please?:(

Regards

Rod

---

### Post by Malac on 2008-07-24
-20 kernel is buggy on some machines
 
press 'Esc' key and boot into -19 kernel and uninstall -20 kernel in synaptic then disable 'proposed' repos in your software sources, these are for people to test stuff who know what they are doing and can get there system back if there is an error.

---

### Post by Rodhill on 2008-07-24
So when I see the 'system starting' words on the black screen, I press escape and then what? Sorry I'm new to Linux.

Rod

---

### Post by sdennie on 2008-07-24
> **Rodhill said:**
> So when I see the 'system starting' words on the black screen, I press escape and then what? Sorry I'm new to Linux.

Rod

Then use the arrow keys to select the kernel that ends in -19 and not -20 and press Enter.  Also, as Malac said, as a new user, you should really disable the proposed repository via System->Administration->Software Sources->Updates.

---

### Post by Rodhill on 2008-07-24
I pressed escape and found the kernels list:) but my keyboard wont move up or down to highlight -19 kernel to boot up. The keboard and mouse are wireless. Would connecting a wired keyboard overcome this?

Thanks

---

### Post by Malac on 2008-07-25
> **Rodhill said:**
> I pressed escape and found the kernels list:) but my keyboard wont move up or down to highlight -19 kernel to boot up. The keboard and mouse are wireless. Would connecting a wired keyboard overcome this?
 
Thanks
Should do, some usb keyboards work from bios some don't depends on the bios.

---

### Post by Rodhill on 2008-07-25
Thank you everyone:popcorn: All sorted and working fine!

Rod

---

