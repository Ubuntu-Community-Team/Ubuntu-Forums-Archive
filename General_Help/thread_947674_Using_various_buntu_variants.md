---
title: "Using various *buntu variants"
date: 2008-10-14
forum: General Help
---

### Post by Gonz_91 on 2008-10-14
Hey everyone!

I've been thinking I'd like to try kubuntu intrepid, but it's kind of sluggish on a VM, since I don't have a top-o-the-line computer.

So, my question is concerning GRUB: installing another *buntu variant, in another partition, would it cause GRUB to be reintalled? In that case, which menu.lst would it use? Do I risk losing access to the ubuntu installation I already have?

thanks in advance

---

### Post by brianfreytag on 2008-10-14
You can choose it not to install the grub, but then the new Ubuntu flavor will not show up in the current grub.

The best way to do it is to back up (or print) the current grub loader /boot/grub/menu.lst, install the new flavor on the second partition, then move the other flavor menu.lst entries into the new flavors menu.lst.

This will allow you to boot into both.

Make sure you don't just move the normal entry, but the failsafe entry as well just in case you have trouble with the old flavor.

---

### Post by Gonz_91 on 2008-10-14
ok, thank you very much for your help ;)

---

### Post by bodhi.zazen on 2008-10-14
You might wish to look at this thread as well (a number of ideas)

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

---

