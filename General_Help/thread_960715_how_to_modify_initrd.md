---
title: "how to modify initrd"
date: 2008-10-27
forum: General Help
---

### Post by francisc1701 on 2008-10-27
Hi there!

How can I modify a file contained in /boot/initrd.img-2.6.24-19-generic, say "conf/conf.d/resume" ? I found some instructions on how to extract the initrd, but they didn't say how to repack it.

Any help will be greatly appreciated.

---

### Post by didac on 2008-10-29
Your initrd scripts -- the ones used to make your present initrd -- are stored in /etc/initramfs-tools Modify them as of your liking. Once you are through, make the new initrd by typing:

    sudo update-initramfs 

Reboot and test it. It should keep a backup of the former one, in case you get into trouble. Or back it up by yourself before messing.

---

### Post by francisc1701 on 2008-10-29
/etc/initramfs-tools contains mostly empty directories, but the file I wanted to modify in the first place (conf.d/resume) is there.

Thanks for your advice, didac

> I found some instructions on how to extract the initrd
They used cpio to extract the files, they don't say how to put it back together, and until now I did not think ](*,) about reading the cpio manual - turns out cpio can copy files into archives.

---

