---
title: "Master Boot Record Error - Press a Key"
date: 2008-11-22
forum: General Help
---

### Post by Apu85 on 2008-11-22
I've installed 8.04 after not using Ubuntu for ½ a year.

When I start up my computer i get "Master Boot Record Error - Press a Key".

When I press a key the Grub loader begins and ubuntu starts up perfectly.

However the message at the beginning is a bit annoying. How do I fix it?

Thanks in advance.

---

### Post by caljohnsmith on 2008-11-22
How about posting the output of:
```
sudo fdisk -lu
```
And also do:
```
sudo dd if=/dev/sda count=20 | gzip -c > ~/Desktop/sda.MBR.gz
```
And please attach the small "sda.MBR.gz" file on your desktop to your next post.

---

