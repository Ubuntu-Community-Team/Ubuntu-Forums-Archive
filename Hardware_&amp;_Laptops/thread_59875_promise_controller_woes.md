---
title: "promise controller woes"
date: 2005-08-25
forum: Hardware &amp; Laptops
---

### Post by CDX74 on 2005-08-25
I just bought a nice new WD raptor for ubuntu to run on with a PROMISE Sata300 TX2+ PCI SATA /IDE Controller Card, but much to my dismay i find that when i try to install ubuntu, it says that it cannot find any hard drives to install on. 

When i boot from a live CD (even tried breezy) and go to the device manager it doesn't seem to recognize the card properly. 

I know the HD and controller work because i installed win2k on them. 

Any ideas, i searched the forums like mad but my only lead was compiling a kernal - would that do the trick?   i'd really like a simple solution tho :)

with red hat i believe you can select drivers at the install stage, can i do that with ubuntu?

and as a last resort i could return the card and get a much cheaper SIIG controller card. has anybody had any luck with those?

---

### Post by CDX74 on 2005-08-26
bump  :(

---

### Post by s_p_a_r_k_y on 2005-08-26
I recently had a problem with a raid controller and sata drives with ubuntu. It seemed that the kernel didn't support the model I had, but a newer kernel did. I was not about to use Breezy for a production system, so I had to use fedora (ewww rpms) which did have a kernel which supported it. Check google and see if you find anything of value. Sata is relatively new and thus probably needs more work to support all kinds of raid controllers for it

---

