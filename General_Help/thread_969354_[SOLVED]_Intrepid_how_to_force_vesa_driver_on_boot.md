---
title: "[SOLVED] Intrepid: how to force vesa driver on boot"
date: 2008-11-03
forum: General Help
---

### Post by jonathanmotes on 2008-11-03
I had to install Ubuntu using the alternate disc because the live disc would not work. Now it hangs right after I log in. 

I suspect it is a problem with the video driver, so I need to try to make it use the Vesa driver, but the video line in the xorg.conf only says "configured video driver". Should I replace that with the word "Vesa"?

Thanks!

---

### Post by bwhite82 on 2008-11-03
Make sure the following lines are in your Xorg.conf:

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"vesa"
EndSection

---

### Post by jonathanmotes on 2008-11-03
Thanks for the quick reply! 

Another question: Recovery mode mounts the filesystem as read only. How can I change that so that I can write the changes to the xorg.conf file?

---

### Post by bwhite82 on 2008-11-03
> **jonathanmotes said:**
> Thanks for the quick reply! 

Another question: Recovery mode mounts the filesystem as read only. How can I change that so that I can write the changes to the xorg.conf file?

Hmmm..never heard of this. At any rate, you can unmount the drive (umount command) then remount (mount command) with read/write flag -rw I think. Look at: man mount

---

### Post by jonathanmotes on 2008-11-03
I'm having trouble figuring out how to mount/umount. I'll try again later tonight (I've got a class soon).

I once got a warning that I needed to do a disk scan (fstab or something). Maybe that is the reason it is read only. Do you know how to do a disk scan from the terminal?

Thanks!

---

### Post by bwhite82 on 2008-11-03
fsck

---

### Post by jonathanmotes on 2008-11-03
Thanks Soldierboy! You were a great help. I succeeded in applying the vesa driver after doing the disk scan. I later discovered the root of my problem was conflicting video cards, not the driver, but I could not have determined that without applying other drivers!

---

