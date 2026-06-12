---
title: "How do you uninstall the OS?"
date: 2011-05-25
forum: Hardware
---

### Post by Bjorgan on 2011-05-25
I managed to install two OS, because the first install failed. How do I uninstall one of them? And is there a chance of reversing disk drive splits? What I mean, is that I divided my secondary disk drive into two parts, is there a chance of adding those two together again?

Sorry for my English, btw..

---

### Post by aphatak on 2011-05-25
I am sure there is a way to get rid of the unwanted OS (and the partition in which it is istalled).  The steps would be -
[LIST=1]
[*]Boot into the OS you are using (and want to continue using), mount the partition that contains the usused OS, and copy the data you want to a safe place.  Unmount the unwanted partition.
[*]Start gparted (System -> Administration -> gparted).  If you don't have gparted, you can install it easily enough with```
sudo apt-get install gparted
```
[*]Delete the unwanted partition.  If this unwanted partition is mentioned in /etc/fstab, get rid of those references.
[*]Update your grub menu with ```
sudo update-grub
```At this point, I should reboot, and confirm that your unwanted OS does not appear in the Grub menu, your normal (one you want to retain) does, and you can boot into it normally.

[*]Restart (yes, again), but this time boot with a live CD.  Start gparted (live CD normally has gparted).  Expand the partition with the required OS to occupy the vacated space (you might have to move and expand that partition).
[*]Once you have the partitions exactly as you want them, restart.  This time, you should boot from your hard drive (not from the live CD).  You should be able to confirm that your unwanted OS and partition are gone, and that the vacated space has been used wherever you want it used.
[/LIST]
Moving partitions and/or re-sizing them does not touch the UUID (the handle which Grub and fstab uses to identify your partitions).  However, playing with partitions always scares me a little, so I suggest taking a backup of all important stuff on your hard drive before embarking on this (any self-respecting lawyer would tell you to update your will before you undergo heart-surgery, right?).  Also, google around for details until you are comfortable with the steps and the commands before you do this in anger!

Oh, and I assumed the OS you want to retain is Ubuntu - the steps I listed above are based on that.

---

### Post by Bjorgan on 2011-05-30
Thanks for help ! I haven't expanded the OS partition yet, but everything seems to work so far. Again: Thanks, saved me for a lot of work ! :)

---

