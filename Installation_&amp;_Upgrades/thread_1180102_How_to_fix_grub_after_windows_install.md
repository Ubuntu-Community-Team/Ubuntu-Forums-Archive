---
title: "How to fix grub after windows install"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by Swatfoot on 2009-06-06
I found this information very help full after reinstalling vista on the same drive Linux is on.


Recovering GRUB after reinstalling Windows

As above, when Windows is reinstalled, the master boot record will be overwritten. This can be avoided by backing up the boot sector, by following the instructions from step 2 in the above section 'Installing Windows After Ubuntu'. An alternative method, which has the advantage of not requiring forward planning, is to use the Ubuntu LiveCD to reinstall the GRUB boot sector, here are step-by-step instructions, to be run after Windows has been reinstalled:

   1. Boot into a LiveCD
   2. Open a terminal
   3. Open the GRUB Command line utility by typing 

sudo grub

   4. Tell GRUB where your Ubuntu partition is by entering 

root (hdA,B)

Where 'A' is the hard-drive number, starting at 0, and 'B' is the partition number, starting at 0. For example, if Ubuntu was installed on the second partition of the first hard-drive, the command should be

root (hd0,1)

   5. Tell GRUB which drive to put the boot sector on 

setup (hd0)

(replacing 0, as above, if a drive other than the first is used as the boot device)

   6. Leave the GRUB Command line 

quit
             ;)

---

