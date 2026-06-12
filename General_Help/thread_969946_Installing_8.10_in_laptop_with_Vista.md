---
title: "Installing 8.10 in laptop with Vista"
date: 2008-11-03
forum: General Help
---

### Post by Jayhawker on 2008-11-03
Please, is there any risk installing 8.10 in a laptop with Windows Vista. I mean installing it fully, not inside windows and all that. How should I install it without spoiling Windows system?

---

### Post by TeXtonyx on 2008-11-03
Yes! First use Vista to resize its own partition. That creates
unallocated space on your drive. If you decrease the size of Vista
by 20GB, then a 20GB free space to fit Ubuntu into will be created.

It is up to you whether you try the newish 8.10 or more tested 8.04
When the Ubuntu live cd asks you where to install Ubuntu, pick the
option 'largest free space, guided'. It will pick the space you created.
It will not install over Vista or resize Vista with a Linux tool.

In Step 7, choose Advanced. Deselect hd0 which writes to the MBR.
Choose install grub to the /boot partition. This will keep Vista
safe from having its MBR overwritten by Ubuntu. This keeps Vista
booting intact in case you uninstall Ubuntu or Ubuntu fails. 

You won't be able to boot Ubuntu yet. From Vista, download Easybcd
(free) and install it. Run it and under Linux, add your Ubuntu
boot partition which should be listed. That adds Ubuntu to your
Vista bootloader menu options. 

I think it is a good idea to add Vista to the grub menu.lst options*
so that you could boot Vista from grub also as a backup. Download
and burn the Super Grub disk which is very handy. Suppose your
Vista bootup gets corrupted. You can use the Super Grub disk to
boot Ubuntu and have an alternate connection method. This way,
neither OS depends on the health of the other OS, so it's more
flexible and easier to troubleshoot. If Ubuntu is installed to 
MBR and Ubuntu fails, then you have to find your Vista install cd
to run bootrec to repair the MBR to Vista compatibility. I think
that is a bigger PITA than the smaller pita of installing grub to
the Ubuntu boot partition. My suggestion is a little more work
but is made in the spirit of: an ounce of prevention is worth a
pound of cure. There will be no spoilage. [*should be automatic]

---

