---
title: "After deleting Windows partition, swap isn't activated anymore"
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by sparklingspecks on 2009-02-14
Hi, I recently removed my Windows partition, so that I would have more space for my Linux partition. I did this with Gparted from the Intrepid live CD. As my disk layout looked like this: ext3|swap|ntfs, I had to move swap back to make ext3 larger. At some point after that I noticed that Ubuntu starts with scrolling text instead of the Ubuntu logo and that swap wasn't automatically activated anymore (I can, however turn it on per session in Gparted -- that doesn't help with swap not being there when waking up from hibernation, though).
Can anyone help me with this? Thanks in advance.

---

### Post by Pumalite on 2009-02-14
Check UUID in /etc/fstab and modify it as nessesary
Find out with:
```
blkid
```

---

### Post by sparklingspecks on 2009-02-14
Thanks.

---

### Post by caljohnsmith on 2009-02-15
If you want to get back your Ubuntu splash screen, I would recommend changing the UUID of your new swap partition back to what it was originally. That way you won't have to modify /etc/fstab or the /etc/initramfs-tools/conf.d/resume file, and also regenerate all your initrd images. How about posting the output of the following:
```
sudo blkid -c /dev/null
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
sudo fdisk -lu
```
And we can work from there if you want.

---

