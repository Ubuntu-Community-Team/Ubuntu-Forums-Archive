---
title: "Unable to mount the selected drive (USB drive)"
date: 2007-02-01
forum: Hardware &amp; Laptops
---

### Post by nekator on 2007-02-01
Hi all, see if someone might help...

I've had ubuntu for about 48 hours (nearly 24 of them trying to install damn 6.06). Before I decided to update this install using update manager I could see and read my USB drive (a sone media, 512 MB, FAT16). After the updates the USB does not pop up automatically and when I go to places-compute and try to manually open it I get this message saying UNABLE TO MOUNT THE SELECTED DRIVE....details:
mount: only root can mount /dev/sdf on /mnt/usb

I must say I've tried to solve this on my own but have not been able t do so...

Something else, before installing ubuntu 6.06 I had partitioned my HD to make space for a FAT32 partition called DATA where I was thinking of saving both my ubuntu and windows files (pdfs, text files, word files, excell files, etc).... 

Again, when I go to places-computer and attempt to open this drive up i get

UNABLE TO MOUNT THE SELECTED DRIVE....details:
error: device /dev/sda3 is not removable

error: could not execute pmount

So now that I find myself loving the whole Idea of migrating to linux I suddenly realize that this ubuntu distro might simply not allow me to work without fear of "windows likebehaviour"...any clues as to how I might solve this...? Sorry about the terrible mood...I actually thought this would be friendlier...

Best adn kindest

---

### Post by glabouni on 2007-02-01
to help us help you should post your /etc/fstab and result of "fdisk -l" command

---

