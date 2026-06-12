---
title: "My partition is now detected as sda2 instead of sda1"
date: 2008-06-27
forum: Hardware
---

### Post by PhrygianCat on 2008-06-27
I resized my partition using gparted so that I can try dual booting, in order that I can play some WinXP based games. It didn't work out since my XPS M1330 is not friendly toward XP. Because of it, what used to be /dev/sda1 has become /dev/sda2 and what used to be /dev/sda2 is now /dev/sda3.

I finally am able to boot again to Hardy after fixing GRUB. However, when I boot up I get some error messages. I'm not sure from what, but I think something is still looking for the original /dev/sda1.

So the big question, is there a way to make Hardy recognize my partition the way it used to be? Or is this just my punishment for looking back at M$ product? Any help is appreciated. Thanks.

---

### Post by lswb on 2008-06-28
Can you post the error message? Just a guess, it seems like you did successfully add another partition to your system; if so, perhaps your swap partition is not now being mounted properly. can you post your /etc/fstab, and the output of:   sudo fdsik -l

---

### Post by PhrygianCat on 2008-06-29
Not sure why, but the error message didn't show up anymore. Not sure if I still have prob;em to resolve. I still don't have sda1, but I guess as far as every is working I guess that is fine. Thanks for helping out lswb.

---

### Post by Ng Oon-Ee on 2008-06-29
Sounds like it was most likely fstab using your udev-assigned names instead of UUIDs.

If there's any more problems post here, most will be more than glad to help =)

---

