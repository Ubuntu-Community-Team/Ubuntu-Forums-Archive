---
title: "HD malfunctioning"
date: 2009-07-08
forum: Hardware
---

### Post by t_ras on 2009-07-08
Hi to all
I have all system in sda1 but /home in sdb1.
sda1 is having problem in some cylinder and the OS makes problems because of it.
I would reinstall but I have a lot of precious data in /home
I have a few questions:
1) is there a way I can reinstall and still keep /home as is? (just by adding the same users or something?)
2) if not - is there a way I can tell the system not to use the bad sectors ,if I get the list someway from FSCK (which BTW was unable to fix anything)?
3) Where does MySQL keep its DB files, I want to be able to copy them away some way.

Thanks for the HELP!

---

### Post by t_ras on 2009-07-08
Hey don't forget me! (poping)

---

### Post by t_ras on 2009-07-10
poping

---

### Post by Dave_Connor on 2009-07-10
I would reinstall and do not format /dev/sdb1 and make a dd image copy of your home partition "sudo dd if=/dev/sdb1 of=whereyouwantyourcopyofhome" just in case.

---

### Post by t_ras on 2009-07-11
Iguess the problem ould be with security, is thers some way ,but just runnin chgroup and chown on all folders, to update to the new ones (userX-> userX, root->root....)

THANKS!

---

### Post by Zeedok on 2009-07-16
You could try [Clonezilla]("http://clonezilla.org/") which I just tried out yesterday due to impending drive failure (I've had some issues too).

---

