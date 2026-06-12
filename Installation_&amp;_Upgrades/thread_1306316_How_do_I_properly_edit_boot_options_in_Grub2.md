---
title: "How do I properly edit boot options in Grub2?"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by dazer26 on 2009-10-30
So I just did a fresh install of kubuntu 9.10 on my desktop.  The one thing I forgot to research before doing the install is how to configure grub2.  Because I have a TV card and a Nvidia video card, after installing the nvidia-glx driver it just boots to a prompt.  In grub I have to add vmalloc=256m to the boot options.  I know I can still edit /boot/grub/grub.cfg, but this isn't how it's supposed to be done with grub2.  I also want the vmalloc to be added to any new kernels that get installed (with grub I always had to manually edit menu.lst after every kernel upgrade).  The file you are supposed to edit is in /etc/default right?  I forget the name of the file as i'm not on my desktop at the moment (at school in the library on my laptop running 9.04).  I took a gander at it before tho and I couldn't figure out where I would put in this vmalloc=256m option.  Any help would be great.  After I edit that file I do a "sudo grub-update" correct?

As well with previous versions of ubuntu if I messed up my video settings I could boot into the recovery mode and one of the options was to reset x settings or something similar, which would let me at least get into a graphical desktop.  This options seems to be missing in 9.10, any idea why?  It's not a huge issue as I can use nano and the command line to edit files, but if I can help it I don't like using the command line as it isn't the 80's anymore...

---

### Post by dazer26 on 2009-10-30
bump

---

### Post by grandtoubab on 2009-10-30
[http://www.gnu.org/software/grub/grub-2.en.html](http://www.gnu.org/software/grub/grub-2.en.html)

---

### Post by kkaldroma on 2010-09-09
**404 - Page Not Found**


No go-grandtoubab

I remembered editing a grub.conf (or something) a while back to increase 'vmalloc' but now after many updates and reinstalls that conf doesn't seem to exist.

Anyone have any updates on this?

---

### Post by ronparent on 2010-09-09
You can do this from a live cd if needed. Find the file system of your install and open /dev/default/grub with gedit. Find the second line reading 'GRUB_CMDLINE_LINUX=' and add your boot parameter(s). Save and you are ready to go (providing it is the right one). Good luck.

---

