---
title: "Grub2 and dual boot configuratiion"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by jheaton5 on 2009-10-23
I have Debian squeeze installed on sda.  I have another drive sdb.  In times past when I have installed ubuntu after debian grub ends up on the ubuntu drive.  I want to install ubuntu 9.04 on sdb but leave boot on sda.  I currently use grub2 to boot debian and have spent a lot of time getting it configured like I want it.  If you can point me to an appropriate resource I would be grateful.
Thanks

---

### Post by dstew on 2009-10-23
I think you do it this way. Install Ubuntu but do not install any boot loader (I think this is step 7, Advanced). This will preserve your grub2 on Debian. When you are done installing, boot Debian, and run **update-grub2**. Supposedly, this will automatically detect your newly installed Ubuntu system and add a menu item for it. See this [Grub2 Basics thread]("http://ubuntuforums.org/showthread.php?t=1195275"). There have been some problems, but generally this works. If it is not working, you can try **grub-install** instead of update-grub2.

There is no longer a menu.lst that you edit. If you want to add an entry "by hand", you write a script and put it in /etc/grub.d/

---

### Post by drs305 on 2009-10-23
I don't think I cover this in Grub 2 Basics but what dstew wrote looks correct to me. As stated, make sure you click Advanced in Step 7. It's easy to overlook.

Make a copy of your grub.cfg file anyway so you have the information if you end up having to copy information from it somewhere later.

---

### Post by jheaton5 on 2009-10-23
Many thanks, guys.

---

