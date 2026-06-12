---
title: "dual boot question"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by stuart.reinke on 2009-04-24
I'm thinking of doing a clean install of Jaunty alongside Intrepid so I can try the ext4 file system. If all goes well and I like how it works, can i remove the intrepid installation and partition without affecting the new Jaunty setup?

---

### Post by btermeli on 2009-04-24
If you don't have  a shared Home folder, yes :)
With Gparted you can do that easily.
May be at the end, you need to install GRUB again, thats all :)

---

### Post by doas777 on 2009-04-24
I think it depends on where your MBR/bootsec are. if it is on the partition where intrepid lives, then you may have to reinstall grub from a live cd after removing that partition. easy enough: [http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+repair](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+repair)

---

### Post by stuart.reinke on 2009-04-24
Thanks for the info. I'll give it a try.

---

