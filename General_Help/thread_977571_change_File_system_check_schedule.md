---
title: "change File system check schedule?"
date: 2008-11-10
forum: General Help
---

### Post by raspa_sete on 2008-11-10
Every time I boot my Ubuntu, the systems starts a file system check.
I have been looking around but I can't find a way to change the schedule for this.

Right now it takes about three minutes to get to the login screen!!!
help please!

---

### Post by iponeverything on 2008-11-10
strange.  It should be set to about every 30 boots, so something else is going on.  When you get to the grub screen hit "e" chose your kernel line hit "e" again and remove "quite" and "splash" from the boot line and then "b" and watch the boot up for strangeness.

BTW this will change the check frequency, though I don't think that that is your problem.

```
sudo tune2fs -c 30 /dev/hda1
```

---

### Post by jerome1232 on 2008-11-10
Except if he is using any fairly recent version of Ubuntu it will be sda1 instead of hda1. All hdd's get sdxx designations.

edit: For clarification some linux distro's will put ide partition as hdxx (meaning hda1, hda2, hdb1, hdb5 and so forth) and sata/scsi drives as sda1 and etc...)

Ubuntu and most distro's with newer kernels just assign all partitions as sdxx (sda1, sda2, sdb1, sdb5 and etc...)

Hope that clears up what I said a bit

---

### Post by raspa_sete on 2008-11-11
Thank you both, althoug I didn't understood what jerome1232 said.

Here's some data:
I'm using: Ubuntu 8.04.1 2.6.24-21-generic

The checking file system says: fsck 1.40.8(13-Mar-2008)

and it checks /dev/sda2 and another one but it went too fast I couldn't see what it said. Nonetheless, its sda not hda so jerome1232 is correct (even if I don't understand what he said)

---

### Post by raspa_sete on 2008-11-13
ups, wrong post

---

