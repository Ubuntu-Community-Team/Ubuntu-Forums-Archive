---
title: "Panic, hd crash"
date: 2005-11-10
forum: Hardware &amp; Laptops
---

### Post by aspak on 2005-11-10
My laptop, that's been running nicely wity ubuntu for about 1 year now, suddenly crashed (or so it seems).
On reboot I get the following message:
UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
then it asks me for root password for maintenance. Trouble is that I've never set any root password, since I only operated the password for my account.. And I can't log in with that one now.

Never had such experiences before, and I hope not my hd is fucked.

Anyone that can point me in the right direction about what to do here?

---

### Post by 23meg on 2005-11-10
First advice: do not write anything on the disk with Ubuntu any other OS. Can you start in recovery mode? If you can, do a fsck there. If not, try a live cd distro such as Slax to do the fsck and rescue your data.

---

### Post by aspak on 2005-11-10
how do I start in recovery mode?

---

### Post by 23meg on 2005-11-10
Choose a kernel option that ends with "recovery" in the grub boot menu.

---

### Post by dmwit on 2005-11-10
Pop in your installation CD and look for the "recovery mode" option.

---

### Post by aspak on 2005-11-10
Tried to boot from the recover kernel image, but same problem. It tries to check the filesystem but after 20% it stops and tells me to check it manually, after having entered a root password.

I'm getting a bit of a panic here..

---

### Post by 23meg on 2005-11-10
No, I don't mean the installation CD (I'm not aware of such an option actually), try booting with the kernel in recovery mode first.

---

### Post by 23meg on 2005-11-10
[QUOTE=aspak]Tried to boot from the recover kernel image, but same problem. It tries to check the filesystem but after 20% it stops and tells me to check it manually, after having entered a root password.

I'm getting a bit of a panic here..[/QUOTE]
Do not panic. Download a light version of [Slax]("http://www.slax.org"), which will most likely detect and mount all your drives, and do the fsck there.

---

### Post by aspak on 2005-11-10
Ok, thanks, I can try that.. Do you think I can use the live version of ubuntu as well? I have that on cd so...

---

### Post by 23meg on 2005-11-10
Most probably you can, but I've had problems mounting drives that haven't been cleanly unmounted with the Ubuntu live cd. Slax on the other hand immediately recognized all my drives (fat32, ntfs, ext3) and I was able to rescue all my data by simply copying it.

---

### Post by aspak on 2005-11-10
Ok, thanks again man.. The ironi here is that I was about 1 hour from taking backup from 24 hours of php programming, when this happened. But I'll try to get whatever I can from my disc, and then maybe I have to reinstall ubuntu (or slax).

If you ever come to Norway I'll buy you a beer :)

---

### Post by 23meg on 2005-11-11
Hey thanks! I hope all that's at stake here is 24 hours and no more. And hope Slax worked for you?

---

