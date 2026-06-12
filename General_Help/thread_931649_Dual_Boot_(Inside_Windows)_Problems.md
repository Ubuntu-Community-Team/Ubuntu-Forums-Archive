---
title: "Dual Boot (Inside Windows) Problems"
date: 2008-09-27
forum: General Help
---

### Post by ArcDarkWolf on 2008-09-27
Hello there,
Now I absolutely adore Ubuntu and Linux too, but I had to remove it at one stage because I was using a dual boot, and I needed to use my other hard-disk. Somewhat oddly enough, Windows wouldn't allow me to un-install it from the All Programs section, nor would CCleaner do it either, so I had to manually delete the files within my drive. However that left the option to boot Ubuntu on my boot screen. Obviously it won't do anything, and takes me back to the Boot screen. I know this is more of a Windows Orientated query, but any help would be nice.

Using Windows Vista Home Premium SP1 < If that's any help.

Again, any help is help and would be much appreciated.
Thanks
--ArcDarkWolf

---

### Post by TeXtonyx on 2008-09-27
You have to reinstall the Windows standard MBR. You can do that by running fixmbr
from the Recovery Console if you have the Windows install CD, or you can download
and install ms-sys, using:  sudo dpkg -i ms-sys_2.1.0-1_i386 or perhaps find where you
downloaded and saved ms-sys and double-click on it with the file browser and then
provide your password.  	You can Google for the alternate file locations or use  
[http://debian.cs.binghamton.edu/debian/pool/main/m/ms-sys/](http://debian.cs.binghamton.edu/debian/pool/main/m/ms-sys/)
ms-sys_2.1.0-1_i386.deb	07-Oct-2005 09:02 	 20K
Read the instructions, Windows XP or Vista is usually a NTFS file system,  32-bit. Actually, I'm not sure that ms-sys is tested for Vista so using your Windows install CD and Recovery Console is a more reliable approach.

---

### Post by phpx2pperl on 2008-09-28
Using synaptic manager, it showed already installed.

Command:
root@phpx2pperl-laptop:/home/phpx2pperl# find / -name ms-sys -print

Cannot find this?

---

### Post by ArcDarkWolf on 2008-10-03
> **TeXtonyx said:**
> You have to reinstall the Windows standard MBR. You can do that by running fixmbr
from the Recovery Console if you have the Windows install CD, or you can download
and install ms-sys, using:  sudo dpkg -i ms-sys_2.1.0-1_i386 or perhaps find where you
downloaded and saved ms-sys and double-click on it with the file browser and then
provide your password.  	You can Google for the alternate file locations or use  
[http://debian.cs.binghamton.edu/debian/pool/main/m/ms-sys/](http://debian.cs.binghamton.edu/debian/pool/main/m/ms-sys/)
ms-sys_2.1.0-1_i386.deb	07-Oct-2005 09:02 	 20K
Read the instructions, Windows XP or Vista is usually a NTFS file system,  32-bit. Actually, I'm not sure that ms-sys is tested for Vista so using your Windows install CD and Recovery Console is a more reliable approach.

One major problem with your fix. I don't have any Windows Vista Home Premium discs, as my laptop was:
A replacement
Pre-loaded with both Windows and Acer software.

Thanks... but I already ruled this option out. Also, I neglected to mention (clearly) that it's the inside Windows install, not a complete dual boot.

The options on my dual boot screen (the two options to start Ubuntu) would do exactly the same thing, since the Ubuntu "directory" was on one drive both times. So if I installed it **again**, it wouldn't matter which one I chose, since all three would start the same Ubuntu Install.

---

