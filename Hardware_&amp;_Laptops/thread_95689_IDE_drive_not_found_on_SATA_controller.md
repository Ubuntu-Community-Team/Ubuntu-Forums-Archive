---
title: "IDE drive not found on SATA controller"
date: 2005-11-27
forum: Hardware &amp; Laptops
---

### Post by bioboi69 on 2005-11-27
I have breezy installed on my 1st hdd (SATA), but now my 2nd hdd (PATA) won't detect. both detect fine in windows. system is running on an abit ax8 motherboard.

any help greatly appeciated.

---

### Post by metoo on 2005-11-27
What do you mean with not detected? Not mounted or not detected (seen) by the kernel?

Do you have an entry in the /media directory for it?

Can you access it with
sudo cfdisk /dev/hda
Assuming, that it is the master on the 1st IDE channel.
(Be careful, don't do anything here, see if the drive is recognized and then exit)

---

### Post by bioboi69 on 2005-11-28
drive isn't detected by the kernel. it's plugged into IDE1 port. as far as I know ports IDE1 and IDE2 run through my vt8237 controller. I've had the same disk running fine in linux from IDE3 which runs from a vt6421 controller, but I need that for my optical drives as they won't operate properly on the IDE1 and IDE2 ports. been driving me mad for a while now.

---

### Post by bioboi69 on 2005-11-29
no one else? :confused:

---

