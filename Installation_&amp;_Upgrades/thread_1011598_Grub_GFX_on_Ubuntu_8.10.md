---
title: "Grub GFX on Ubuntu 8.10??"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by poopboypat on 2008-12-14
Ok I'm trying to install Grub GFX with ubuntu 8.10 with all the latest updates. I have been following this link.

[http://tuxenclave.wordpress.com/2008/01/18/how-to-install-gfx-grub-in-ubuntu/](http://tuxenclave.wordpress.com/2008/01/18/how-to-install-gfx-grub-in-ubuntu/)

Now when I get to “find /boot/grub/stage1” I get get an error.  “Error 15: File not found ”

Is there anyway I can install Grub GFX?  I really don't like the current Grub.  If I can't install it does anyone have any other suggestions for a good boot loader?

---

### Post by caljohnsmith on 2008-12-15
One thing to be careful of is to use the latest gfxboot package; Intrepid now formats its ext3 partitions with an inode size of 256 bytes, whereas previous versions of Ubuntu used 128 byte inode sizes. If you try to use an older version of Grub to boot an Intrepid partition, Grub will choke and spit out a Grub error 2. Here is a link to the latest gfxboot package that should work fine with Intrepid:

[http://sidux.com/debian/pool/main/g/grub-gfxboot/](http://sidux.com/debian/pool/main/g/grub-gfxboot/)

How about trying that first, and if you still run into problems installing it, let me know.

---

### Post by poopboypat on 2008-12-15
ok, i got grub GFX to work, but the size is all wrong.  I am only seeing the top left of the boot screen. So im missing about 3/4 of the image.  Is there a way to change the resolution of the image or the acctuall way grub is booted?

---

### Post by hjacker on 2009-05-27
I haven't found any decent tutorials how to install Grub gfx on ubuntu 9.04 without crashing everything nearby. :(

---

### Post by hjacker on 2009-05-27
Oh, sorry, this version of GRUB really worked. Thanks.

---

### Post by hjacker on 2009-05-27
Anyway, it all worked with default Synaptic themes, yet fails with all the ones I found on the web. -_-

---

