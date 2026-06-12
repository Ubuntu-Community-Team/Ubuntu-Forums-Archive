---
title: "Installing from hard disk ... cant find partitioner"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by true_friend on 2009-02-17
Hi folks
I somehow managed to boot from ISO image of kubuntu 8.10 live cd. But I am unable to install it due to the fact that there is no partitioner or more appropriately the installer cannot display the harddisk on which the system is going to be installed. There is simply a black window on 4th step. I tried [this tutorial]("http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html") and then added the boot entry from [this tutorial]("http://deepbluespaces.blogspot.com/2008/07/install-ubuntu-804-from-hard-disk.html"), I couldn't even boot first following 1st tutorial then changing the original boot command to 2nd's 
--------------
title Install Ubuntu
root (hd0,4)
kernel /vmlinuz boot=casper iso-scan/filename=/ubuntu-8.04.1-desktop-i386.iso
initrd /initrd.gz
--------------
I managed to boot into KDE desktop and ran the installer but...:( as i mentioned the installed can't locate the harddisk table.
Any ideas to improve this situation? Do I need the alternate install cd for this purpose?
Regards

---

### Post by redroad55 on 2009-02-17
Check the Integrity of install disk if you haven't already by booting it and choosing the check cd option ..Also make sure the HD is being seen in Bios ..

---

### Post by true_friend on 2009-02-17
Itegrity wasn't right thats a fact, So I tried to install it from hard disk. Above given links are basically to install directly from iso image. So I asked what is and where is something wrong I am able to boot from this iso image from within windows through windowz version of grub but cannot install after booting and going to live cd mode (which is actually live hard disk mode perhaps).
Regards

---

