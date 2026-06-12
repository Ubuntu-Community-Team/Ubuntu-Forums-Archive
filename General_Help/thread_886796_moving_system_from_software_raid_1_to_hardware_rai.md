---
title: "moving system from software raid 1 to hardware raid 1"
date: 2008-08-11
forum: General Help
---

### Post by Fredrik_b on 2008-08-11
My setup today

System on 2 x 40GB IDE drives witch is software raided using alternative ubuntu cd 8.04

On this sytem I have created en raid 5 array from 4 750GB sata drives located on an fasttrack s150 tx4 sata raid/controller card.

One problem I have is that the computer stucks saying that no array has been configured when that fasttrack card loads, as there shuldent be sins I created the array using mdadm.

But this is still a problem when you remotley restart the computer, sins it will not boot into ubuntu unless you press ESC.

Sins I wanted to replace my IDE drives (2x40GB 2.5") with SATA drives (2x80GB 2.5") I was thinking of putting the to new sata drives on the controller card and create an raid 1 array and move 2 of the 750 to the motherboard. creating an system from scratch is no problem.

But I want to retain the raid 5 array. I assume I cant clone the old 40 GB drives if I am going to use hardwere raid.

If I install a new version of ubuntu on a clean hardwere raid 1 array can I just copy the mdadm files from the old installation of ubuntu to the new instlation, and rebuild the array?

---

### Post by fjgaude on 2008-08-11
If I understand you correctly, you don't have to rebuild the raid5 array.

After you have installed the new Ubuntu, simply install mdadm and then run:

```
sudo mdadm --assemble --scan
```

and a new /etc/mdadm/mdadm.conf file will be created. Now you can mount the raid5 array and place a line in your fstab file to automount on reboot.

Let us know if you have problems.

---

### Post by psusi on 2008-08-15
It sounds like you don't have a hardware raid at all, but rather a fake hardware raid card, and you aren't even using the fake raid support.  Instead you configured a Linux software raid, and it sounds like the bios complains and wants you to press escape to continue when it does not find any fake raids.  Just disable the fake raid option in the bios so it doesn't look for one.

---

