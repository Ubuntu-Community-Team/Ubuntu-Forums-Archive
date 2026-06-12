---
title: "Borked my Install"
date: 2008-08-31
forum: General Help
---

### Post by rlanham on 2008-08-31
So I messed and forgot that deleting my Vista partition before running LVPM would leave me without a Bootloader. So now I can't boot into any of my OS's which is just the one Wubi Ubuntu install. I am currently booted into a Live CD and I have tried using the GRUB instructions on installing it but it wont find any stages. The problem is that the Ubuntu is all in a virtual file system since it was a Wubi install. Is there a way to mount the Wubi FS system and CP everything over to my /dev/sda5 and then mount and create GRUB from there?

---

### Post by rlanham on 2008-08-31
Ok so I have mounted the virtual disks root, home, and usr into /vdisk ... I then mounted my new linux partition /dev/sda5 to /mnt/root and cp -aR everthing from the /vdisk to /mnt/root.

Now I just need to figure out how to get grub installed and working.

---

### Post by ago on 2008-09-03
> **rlanham said:**
> Ok so I have mounted the virtual disks root, home, and usr into /vdisk ... I then mounted my new linux partition /dev/sda5 to /mnt/root and cp -aR everthing from the /vdisk to /mnt/root.

Now I just need to figure out how to get grub installed and working.

You can use the following script and/or look at the code

[https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=wubi-move-to-partition](https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=wubi-move-to-partition)

---

### Post by llh11456 on 2008-09-06
The Runner is a moving, sincere [Age of Conan Gold](http://www.usfine.com/Age-of-Conan-USA-c-151.html) piece of art. Despite that, most audiences might not have even noticed that it went through the theaters like a desert breeze. It&#8217;s made a modest showing internationally, and pulled in $15.4 million in its limited [Age of Conan Power Leveling](http://www.usfine.com/Age-of-Conan-US-PL-c-146.html) US release. Critics, however, remained mixed, although most of the negative reviews placed the film up against the poetic genius of its source material ?C the best selling novel by Khaled Hosseini.

---

