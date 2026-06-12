---
title: "boot problem with 10.04 on netbook"
date: 2010-07-27
forum: Hardware
---

### Post by mrov04 on 2010-07-27
I recently installed 10.04 on my HP mini. Everything was ok in the installation and the disk was correctly partitioned. I need to use also windows 7. 
Now when I boot from grub if I choose windows7 it goes rigth, but if I want to boot into ubuntu... something strange happens. Frequently the system stops and I see only a black screen ... Even more strange sometimes ubuntu starts and works very fine.
I found that when the system does'nt boot I see that the light indicating the activity of the hard disk does not appear, it is like grub does not find the partition. But sometimes it works! :(
Could you please help me?

                                 M.

---

### Post by wojox on 2010-07-27
Try [Reinstalling Grub 2 from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Then boot into Ubuntu and run

```
sudo update-grub
```

---

