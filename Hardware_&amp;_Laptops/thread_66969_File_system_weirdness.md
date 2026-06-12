---
title: "File system weirdness"
date: 2005-09-18
forum: Hardware &amp; Laptops
---

### Post by PaganHippie on 2005-09-18
I just replaced the 4 GB HDD in my Ubuntu system with a 200 GB unit. Used partimage to transfer everything from the old drive to the new one, then re-installed grub. Boots up fine, everything works. There's just one little problem... the file system on my new 200 GB HDD still thinks it only has 4 GB. cfdisk confirms that the partition table is OK, /dev/hda1 is 200 Gb as it should be.

Short of reformatting the drive & reinstalling Hoary from scratch, is there a way to get the extra space back?  ](*,)

Thanks in advance....

---

### Post by Ptero-4 on 2005-09-19
[QUOTE=PaganHippie]I just replaced the 4 GB HDD in my Ubuntu system with a 200 GB unit. Used partimage to transfer everything from the old drive to the new one, then re-installed grub. Boots up fine, everything works. There's just one little problem... the file system on my new 200 GB HDD still thinks it only has 4 GB. cfdisk confirms that the partition table is OK, /dev/hda1 is 200 Gb as it should be.

Short of reformatting the drive & reinstalling Hoary from scratch, is there a way to get the extra space back?  ](*,)

Thanks in advance....[/QUOTE]
 First check your BIOS. Some older computers tend to have limits in the HD capacities. Then check the program you used to clone your HD and specially the version you used. Some programs (or some older versions of known-good apps) tend to make the destination HD partition of the size that your old HD had.

---

### Post by PaganHippie on 2005-09-19
The PC is a Dell Dimension 2400 & it recognises the HDD just fine. The version of partimage I used is the one in the Ubuntu Hoary repositories, 0.6.4, which is also the current 'stable' version according to the partimage website.

I should also mention that, before the image restore, I used cfdisk to create a 200 GB partition & then formatted it with mkfs, and it came through as expected, a 200 GB file system.

If I ***have to*** reformat & reinstall, I will, but I'm really hoping that it's possible to avoid that. I've spent a good deal of time & effort getting my setup just the way I want it, & I'd really rather not lose all that work. :-|  Is there any way to get Ubuntu to re-count the number of blocks in a partition?

---

