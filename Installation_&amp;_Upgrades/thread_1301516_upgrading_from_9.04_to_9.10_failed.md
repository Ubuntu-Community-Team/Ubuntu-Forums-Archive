---
title: "upgrading from 9.04 to 9.10 failed"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by borsotti on 2009-10-26
I have upgraded a 9.04 installation to a 9.10 using the recommended update-manager -d command.
The result was a disaster. It cannot even boot now.
Now I have two options: reinstall 9.04 from CD or
install 9.10 from CD.
However, the installer warns that: "The installer is not designed to re-install over an existing system."
This means that in order to recover from the failed
upgrade I have to delete the disk partitions damaged,
and then run the installer letting it to create new
ones.
This is a very bad practice because playing with
partitions is quite dangerous.
Does anyone know how to make the installer use existing Ubuntu partitions?

---

### Post by dstew on 2009-10-26
If your problem is that you cannot boot, maybe you just need to re-configure or re-install the boot loader. Do you get a grub menu, or any errors when you boot? Did you install grub2 with 9.10?

---

