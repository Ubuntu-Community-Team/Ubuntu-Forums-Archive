---
title: "Removing/Reconfiguring GRUB"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by sb360 on 2009-04-26
I have just deleted my ubuntu partition from within windows so that I could install another distro but I forgot about grub and now when I boot my computer I get Grub attempting to load followed my grub error 22 and nothing else.

If possible I would like to reconfigure grub to load windows first followed by any other O/S's.

I am currently using a live CD version of the distro I want to install (linux mint) so will installing this fix my problem or are there any other steps I need to take.

How stupid of me.

Thanks in advance

---

### Post by zvacet on 2009-04-26
Installing Mint should fix your problem.For changing default OS on boot read [this.]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS")

---

### Post by Terminating.proprietary on 2009-07-01
I faced a problem similar to this previously. It may have even been the error 22. I fear the steps I want to take on my machine will reproduce this error. Let me try to explain.


Windows Vista is installed on my machine and always has been. I have been using ubuntu linux for quite some time. When I install ubuntu, with windows present, GRUB overwrites the MBR, detects windows, and all is well. However if I were to remove ubuntu, via deleting the partition from windows disk management, there becomes a problem. I do not recall the exact error code as I have not done this in a while, but it definetly does not work.

I have, once again, damaged my Linux installation to a certain extent that I believe it can not be salvaged. I retrieved my data via a live cd, and now am planning on deleting the linux partition. I plan to install virtualbox and try to run ubuntu within windows. I fear when I delete the partition I will face the same error and not be able to boot either operating system. This will force me to do a clean install of vista and start from scratch, which I would really not like to do. 
Hopefully someone has some suggestion or experience with this situation......

---

### Post by Herman on 2009-07-01
Here is a link to a web page that lists quite few ways to change your boot manager or boot loader before you delete Ubuntu, [Uninstall Page]("http://members.iinet.net.au/%7Eherman546/p18.html").

In simple terms, the reason for this problem is that boot loaders come in two or three pieces and the MBR is very small, it doesn't have enough room for a boot loader, but only a small amount of code to make it point to a boot loader or boot manager somewhere else on your hard disk. Since your GRUB boot loader is situated inside Ubuntu, after you delete Ubuntu, your MBR will be pointing to nothing, so you will get GRUB Error 22.

If you want to keep GRUB as your boot manager after you delete Ubuntu, then use your Ubuntu Live CD to delete all the other directories in Ubuntu except /boot and resize your partitions and organize them the way you want them.
That way, your MBR will still be able to point to /boot/grub in what used to be your Ubuntu partition. GRUB does not need to be in an operating system, it can work just as well all by itself. You will need your Ubuntu Live CD when you want to edit your GRUB boot menu.

If you do not want to keep booting with GRUB, but would rather use some other boot manager or boot loader, then install another boot loader or manager in your hard disk somewhere, and install the IPL for it (pointer) to your MBR.

You can make your MBR point to your Windows Vista boot loader again by running your Vista installation CD and use one of the procedures listed on the page I already linked you to, [Uninstall Page]("http://members.iinet.net.au/%7Eherman546/p18.html").

---

