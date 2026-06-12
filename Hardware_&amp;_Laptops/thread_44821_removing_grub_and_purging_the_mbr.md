---
title: "removing grub and purging the mbr"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by transkinetic on 2005-06-27
I have a toshiba laptop and it's literally tearing itsself apart. Chunks of plastic crack and peel off when I open and close the lid. Fortunately, it's under warranty. My only trouble is that I can't wipe linux from it and just reinstall windows because that would cause grub to fail at boot. I'm also worried that there was some fine print somewhere about not installing operating systems other than windows. Is there a way to completely erase all traces of grub and linux from my HD?

I appreciate any feedback.  :grin:

Edit:

On a completely unrelated note, when's breezy coming out? I know there's a release every six months but...when did hoary come out? I'm really psyched for it  \\:D/  \\:D/ !

---

### Post by trivialpackets on 2005-06-27
[QUOTE=transkinetic]I have a toshiba laptop and it's literally tearing itsself apart. Chunks of plastic crack and peel off when I open and close the lid. Fortunately, it's under warranty. My only trouble is that I can't wipe linux from it and just reinstall windows because that would cause grub to fail at boot. I'm also worried that there was some fine print somewhere about not installing operating systems other than windows. Is there a way to completely erase all traces of grub and linux from my HD?

I appreciate any feedback.  :grin:

Edit:

On a completely unrelated note, when's breezy coming out? I know there's a release every six months but...when did hoary come out? I'm really psyched for it  \\:D/  \\:D/ ![/QUOTE]
 You can restore your Windows MBR with (a) W2K or XP install CD, Recovery mode, command >fixmbr or (b) a W98/ME/DOS bootable diskette, command A:\>fdisk /mbr. If you don't have this media, see [www.bootdisk.com](www.bootdisk.com).

This was from :  [http://www.ubuntuforums.org/showthread.php?p=231439#post231439](http://www.ubuntuforums.org/showthread.php?p=231439#post231439)

---

