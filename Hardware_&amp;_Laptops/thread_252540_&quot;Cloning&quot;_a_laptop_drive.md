---
title: "&quot;Cloning&quot; a laptop drive"
date: 2006-09-06
forum: Hardware &amp; Laptops
---

### Post by promet on 2006-09-06
Hello,

I am in the process of slowly upgrading an old Dell Latitude to be my mobile Ubuntu rig. At some point this is going to mean upgrading the meager 4GB stock hard-drive.

I would sorely like to keep this install as is, as I have had to make a lot of obscure customizations to get the hardware and install working properly.

I am looking for suggestions on how to "clone" this drive's data (Grub install, identical bootability - is that a word? :-k  - , etc., bit for bit ,as it were) to a (projected) 20GB replacement drive.

i.e. how would I have to partition the destination drive? Are there reliable tools, methods, voodoo, luck?

The thought of recalling all of the hacked system configs, moving them to a pen drive and having to bootstrap a new install is...super annoying. So I'd like to petition you good folks for any ideas. I am confident in your collective genius... ;)
.
.
.
.

---

### Post by mssever on 2006-09-07
I'll defer the Grub part to someone else, but here's my take on the other part:

Since this is a laptop, I take it that the old drive is /dev/hda and the new one will also be hda. If you keep the same partition structure (ie, identical except for size), then partitions won't be an issue. Otherwise, you only need to modify /etc/fstab and Grub to point to the correct partitions.

Make sure that either a) your transfer medium uses a Linux filesystem such as ext3; or b) you make tarballs and copy those. Otherwise, you'll lose permissions, ownership, and symlinks, which will pretty much hose your system.

If you copy files, be sure to use sudo cp -a (which is recursive, so don't do sudo cp -a /; do it in pieces: sudo cp -a /etc). This will preserve permissions, ownership, and links. And don't forget to use sudo, else errors might creep in.

Another thing: when doing ls to list directories that should be copied, do ls -a to also see dotfiles and dot directories. And be aware that doing sudo cp -a * won't get dotfiles. To get everything, you need sudo cp -a .* *

---

### Post by amo-ej1 on 2006-09-07
Yeah, grub 's the easy part ;-)
```

chroot /mount/point/of/new/drive
grub
> root (hdx,y)
> setup (hdx)
> exit
exit

```

These commands should be run a root.
(i even think it should work without the chroot, but with the chroot it does a double check that you copied everything right).
Then you open a grub prompt, in that grub prompt you select the root device (x = device number, y = partition number, mind that x and y start to count at zero, the root device is the device containing the kernel image it is the / partition or the /boot partition if you have one). setup (hdx) (where x is the device number) will install the MBR and search for the files in the partition you designated as 'root' in the  line above. Exit from the grub prompt and exit from the chroot'ed environment.

---

### Post by mssever on 2006-09-07
> **amo-ej1 said:**
> Yeah, grub 's the easy part ;-)
```

chroot /mount/point/of/new/drive
grub
> root (hdx,y)
> setup (hdx)
> exit
exit

``` 
These commands should be run a root.
(i even think it should work without the chroot, but with the chroot it does a double check that you copied everything right).
Then you open a grub prompt, in that grub prompt you select the root device (x = device number, y = partition number, mind that x and y start to count at zero, the root device is the device containing the kernel image it is the / partition or the /boot partition if you have one). setup (hdx) (where x is the device number) will install the MBR and search for the files in the partition you designated as 'root' in the  line above. Exit from the grub prompt and exit from the chroot'ed environment.
If you have to pull out the old drive to install the new one, you can boot from the live CD for this step.

---

### Post by promet on 2006-09-08
Hey,

Thank you guys very much for all of your input, I am going to use this info when drive prep time comes. Hazzah!

---

