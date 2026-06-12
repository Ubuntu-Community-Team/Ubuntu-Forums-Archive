---
title: "Upgrading from 8.04 to 9.10."
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by davemar on 2009-10-26
As I'm having a few issues with 8.04 not supporting some stuff that exists in 9.xx, I'm planning on upgrading. Is it better to do an upgrade from 8.04 to 9.10, or a fresh install? 

I've got a pretty well established setup with both the generic and rt kernels bootable from grub, and would like to keep this option. Would a fresh install be a pain to keep all this? I've also got Windows XP and Suse installs bootable from grub which I'd like to keep. 

If I do a fresh install, what's the best way of re-installing all the packages I've built up over the past months? 

I've got /home on a separate partition, can I just leave it as it is?

Also am I right in think the full release of 9.10 is out in a few days?

Sorry for lots of questions!

---

### Post by dstew on 2009-10-26
It is usually better to do a fresh install. I don't know if you can directly upgrade from 8.04 to 9.10. You might have to go from 8.04 to 8.10 to 9.04 to 9.10.

As far as your boot setup, if you want to keep your 8.04 system booting with grub 0.97, and add 9.10 to it, you should avoid installing a bootloader when your are installing 9.10. I think it is Step 7, click Advanced, and decline to install the boot loader. However, 9.10 now uses grub2, and if you are a bit daring, you might want to install it. Grub2 is much better at recognizing the other OS's on your system and creating a boot menu for them. If you decide to keep your old grub 0.97, you will have to create new grub menu entries for 9.10 by editing /boot/grub/menu.lst.

If you have a separate /home partition, you can leave it as it is. But, if you want to keep your 8.04 programs running, I would advise using a different user name when you install 9.10. Sometimes, the configuration files generated under 8.04 (under your old user name) will not work well with 9.10 programs. If you use the same user name, the old configurations for same-name programs might be over written when you install 9.10, and make the old programs non-functional.

---

### Post by raymondh on 2009-10-26
Try the Karmic liveCD (live session) first to see if  your issues are solved.

If ok, I second the fresh install.

---

