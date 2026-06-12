---
title: "2 Unbuntus!?"
date: 2008-11-22
forum: General Help
---

### Post by Alfx on 2008-11-22
I logged into Unbuntu like usual, it told me where was a bunch of updates available.

I proceeded to download and install them.

Upon reboot on the Loader, there was the NEW unbuntu version and the OLD unbuntu version!

How do I fix this?

Thanks

---

### Post by beno1990 on 2008-11-22
When you update your kernel, it usually leaves 2 or 3 previous kernel versions as backups to fall back on in case your new kernel doesn't work properly; this is normal.

If you really don't want it, though, just open Synaptic and search for the old Linux image package and uninstall it, just make sure you don't uninstall your current kernel by mistake.

---

### Post by john183 on 2008-11-22
There aren't two copies of Ubuntu installed on your machine, just two Linux Kernels. You can remove the older one if you want. Just do so through Synaptic. Otherwise you can just leave it, it will not cause any issues.

---

### Post by ciscosurfer on 2008-11-22
You could also just edit your GRUB file, commenting out entries you don't want to show on boot.  This way you can revert to a previous kernel quickly if you ever wanted or needed to.

---

### Post by brainiac8008 on 2008-11-22
You can tell GRUB to display only the most recent entry (kernel). This will be a problem if you ever have to use an older kernel because the newer one doesn't work, but I have never had to use the older ones; I like GRUB to look clean. It is your choice.  If you want to keep only the most recent kernel in GRUB, open up the terminal and put in
> 
sudo gedit /boot/grub/menu.lst

Look for
> # howmany=all

and change it to
> 
# howmany=1

Save and exit.

Then, in the terminal, put in
> 
sudo update-grub

to finalize the changes.

If you want another number of entries to appear, for the "# howmany=" in the menu.lst file, just put the number of entries you want instead of 1.

---

