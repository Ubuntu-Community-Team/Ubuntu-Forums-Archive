---
title: "vaio xp recovery disk after ubuntu installation"
date: 2008-04-22
forum: Hardware
---

### Post by danielotto on 2008-04-22
Hi,

I have a vaio vgn sz3xp, which was running windows xp. last week, after a virus, I  decided to install ubuntu, and leave a small partition with windows xp.
I installed 7.10 and everything went fine.
The only thing is that I (or ubuntu itself, as I read on some posts) deleted the recovery partition.
I have two dvd's, one for system recovery and one for applications recovery, that I made when I got the laptop with XP installed.
Now my question is: can I run the system recovery disk to reinstall xp on the ntfs partition that I created with QParted when installing ubuntu, or this will make mess, e.g. writing on MBR, etc?
Any other warnings or known problems?

Thanks a lot

daniele

---

### Post by eotakos on 2008-12-06
if the recovery procedure writes on the mbr, you can still restore grub on it with a ubuntu live cd - the thing is: will the recovery write only on the mbr? or it will mess around with the whole hard drive and therefore the ubuntu partition...

i've just bought myself a vaio and i'll have ubuntu installed in no time. i'm just reading all the articles for the recovery issue so as to know what to expect...

---

