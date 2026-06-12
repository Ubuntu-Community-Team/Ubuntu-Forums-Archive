---
title: "I've hosed /etc/passwd - help!"
date: 2005-11-19
forum: General Help
---

### Post by pheitman on 2005-11-19
I've made lots of changes over the last 8 days. Everything seemed fine. I rebooted finally. Now I can't log in. For some reason the password I've been using since I installed Breezy doesn't work any more. I thought I'd be smart and use the LiveCD, mount the / partition, edit /etc/password to remove the 'x' where my password should be, save it and reboot. Now /etc/passwd is unaccessible to anyone. Rebooting with LiveCD again and remounting the / partition, I can't access /etc/passwd. I get a 'cannot access 'passwd' permission denied' message. I can't ls, cp, mv, rm, vi it - but it's there because I can't copy a backup copy of passwd there. I've mounted the partition rw - I can change the directory permissions for etc to be 777. I just can see or touch passwd. So two questions: first, how do I repair passwd and second, how do I reset my user password so that I can log in again? Although if I could do the first I could probably do the second.

Thanks in advance,

peter

---

### Post by invalid on 2005-11-19
Try selecting the "Recovery" mode from grub, and running the passwd utility from here.

Cheers,
Cb

---

### Post by pheitman on 2005-11-19
Thanks for the quick reply. First, I'm using LILO (with LVM, etc). Does lilo have a recovery mode? Second, the file /etc/passwd doesn't appear to be accessible any more. During boot lots of messages appeared about not being able to access it (so daemons that needed to run as a particular user like clamav failed to start). Do you think it is likely that recover will help?

Peter

[addendum] I figured out that my reiserfs on / had errors. I've used reiserfsck to fix them - but now lvm is messed up. Hopefully I can figure out how to recover from that error. Booting puts me in busybox with no apparent way to mount partitions (logical or otherwise) or to fix errors.

---

### Post by soulestream on 2005-11-19
first dont ever, ever, ever manually edit the /etc/passwd file, unless you really know what you are doing

you can use a livecd

mount the partition
then chroot into the system

run passwd for root and user

soule

---

### Post by pheitman on 2005-11-19
ah - chroot! I've known about chroot but didn't consider how useful it could be to set a password on a mounted filesystem. Thank you. That will help a lot in the future. Unfortunately now I have big lvm and raid1 and reiserfs problems. I'm guessing that my original problem was because of the reiserfs problems. Now I can't boot (my /boot is md raid1, / is reiserfs on lvm on md raid1). Hopefully I can work through the problems one at a time and get this to recover...

---

