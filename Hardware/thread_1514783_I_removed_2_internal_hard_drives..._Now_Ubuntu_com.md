---
title: "I removed 2 internal hard drives... Now Ubuntu complains!"
date: 2010-06-21
forum: Hardware
---

### Post by stinkinrich88 on 2010-06-21
Hello,

I removed two hard drives from my PC (not the hard drive with Ubuntu on), but now when I start Ubuntu, it complains that it can't find my hard drives during boot. I have to press "s" to skip mounting them. 

How do I prevent this from happening? Is it just a case of editing fstab? If so, where is fstab?

Thanks,

Rich

---

### Post by dino99 on 2010-06-21
bios: check the boot order, maybe it have changed

sudo dpkg --configure -a
sudo grub-mkconfig
sudo update-grub

install and use gconf-cleaner (yes to all)

---

### Post by renkinjutsu on 2010-06-21
You probably still have the entries in your /etc/fstab

just remove the drives' respective lines from the fstab file or append the option "noauto"

---

### Post by stinkinrich88 on 2010-06-21
Thanks guys! But which do I choose!?

I don't think BIOS will have anything worth checking as I only have 1 internal hard drive, now.

---

### Post by stinkinrich88 on 2010-06-21
Tried both but only the second solution worked.

Thank you!!

---

