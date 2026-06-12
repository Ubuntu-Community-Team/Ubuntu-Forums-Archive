---
title: "md5sum on iso image"
date: 2009-04-28
forum: Hardware
---

### Post by alkatron on 2009-04-28
Hello

I have Hardy installed on a desktop and on a old laptop accessing internet by the desktop.

I tried to download an iso image but somethig very strange happened

Checksum is different...ok bad download i tried again and again from different source and mirrors but always different and every download has different checksum than the previous.

Also if i copy the image from a folder to another checksum is different.

i run e2fsck but the problem is still here

May be my hd is crashing?
Or.....what other tests may i do?

thanks

Alkatron

---

### Post by alkatron on 2009-04-28
I forget to say that if i download the image with laptop, everything is ok...so it isn't a connection problem...they share it...

Alkatron

---

### Post by jespdj on 2009-04-28
I had a similar problem on my laptop a while ago.

It turned out that the RAM in my laptop was bad. I replaced the memory modules and now it works normally again.

To test your RAM, select the "memtest86+" option in the GRUB menu when you boot your computer. Let the memory testing program run for a few hours. If it shows any errors, then your RAM is bad and you should replace it.

It could also mean that there's a problem with your harddisk.

---

### Post by alkatron on 2009-05-01
> **jespdj said:**
> I had a similar problem on my laptop a while ago.

It turned out that the RAM in my laptop was bad. I replaced the memory modules and now it works normally again.

To test your RAM, select the "memtest86+" option in the GRUB menu when you boot your computer. Let the memory testing program run for a few hours. If it shows any errors, then your RAM is bad and you should replace it.

It could also mean that there's a problem with your harddisk.

Thank you very much it was the ram, I tested it with memtest86 and other tools and it was corrupted, now i cange it and everything it's ok...

Thanks again

Alkatron

---

