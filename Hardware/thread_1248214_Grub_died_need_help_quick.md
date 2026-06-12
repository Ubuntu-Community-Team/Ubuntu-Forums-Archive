---
title: "Grub died need help quick"
date: 2009-08-23
forum: Hardware
---

### Post by linkxs on 2009-08-23
hi, I dual boot windows 7 and ubuntu. When i installed ubuntu 9.04, in grub it made two boot entries for windows 7, called them both windows vista. I've been using ubuntu  the whole day, fixing the problems that were on this laptop, and was finally done, and tried to boot into windows. I chose the first entry, and when windows finally booted up it shown me some windows and big ERROR word in red letters. so, i thought, not a big deal, lemme just boot into the second entry. after reboot, grub gives me error 22 (i think). Right now i'm in the ubuntu live cd, being sad. the partition manager shows no sign of a 160gb ext3 linux partition. in its place it has unallocated space. Restoring grub using this tutorial:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

didn't work, i was stuck after the command: find /boot/grub/stage1 which gives me an error 15. 

Please help if you can. Thanks in advance.

---

### Post by Plumtreed on 2009-08-24
With your 'live CD' can you boot to the grub menu by selecting 'boot to first hard disk drive' from the 'live CD' menu.

---

### Post by linkxs on 2009-08-24
> **Plumtreed said:**
> With your 'live CD' can you boot to the grub menu by selecting 'boot to first hard disk drive' from the 'live CD' menu.

Well all that's gonna do is try to boot from my hard drive. as i said, my grub is dead.

---

### Post by Plumtreed on 2009-08-24
In my experience, it can boot to the grub menu, which may not solve your problem, but, it will, at the very least, prove that your grub is 'dead'. This is unlikely! On the other hand, if it does come up with the menu you know where you are. 

Suit yourself, don't try it.

---

### Post by linkxs on 2009-08-24
I tried it, got error 22.

---

### Post by Plumtreed on 2009-08-24
Perhaps using the 'Super Grub Disk' might get it to boot. (google for it)

I have had a very similar problem but with Vista. However, since I could boot to Grub, in the end, I used the 'recovery' partition in Vista to put the PC back to factory settings and then re-installed 9.04.

There may be more sophisticated ways of doing it but that got the job done!

---

### Post by linkxs on 2009-08-24
well, i couldn't find a good enough solution quick enough so i decided to just reinstall everything. thanks for help though.

---

