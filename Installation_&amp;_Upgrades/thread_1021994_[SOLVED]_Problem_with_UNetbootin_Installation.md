---
title: "[SOLVED] Problem with UNetbootin Installation"
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by Hornet.ch on 2008-12-26
Hello everybody

I got a new Samsung NC10 netbook this week and wanted to install Ubuntu on it. Unfortunately, I don't have enough capacity on my USB flashdrive, so I can't use the Live-USB method.

Then I found the tool UNetbootin. I used it in Windows with the ubuntu-8.10-desktop-i386 ISO. I could also boot the livecd and run the installation wizard. The problem was, that the partition table was empty. After some searching I came to the solution that I had to run the following command before running the installer:

```
sudo umount -l -r -f /dev/sda2
```
(sda2 is the windows partition where UNetbootin was installed)

Finally, I managed to run the installation program. But after rebooting I discovered that something went wrong: The grub entry to start Ubuntu is missing. There are only the two entries for Windows and Ubuntu Memtest. I really have no idea what to do now.

I hope somebody could help me.

Thanks in advance

---

### Post by Hornet.ch on 2008-12-27
So, after some trying I found a workaround, but I still don't know the cause of the problem.

The problem was that the installer didn't install the kernel. I booted the live cd with UNetbootin, chroot'ed into the new installed environment and installed the actual kernel with apt.

Now everything works fine :D

---

### Post by gnaunited on 2009-04-05
I would recommend doing a apt-get install ubuntu-desktop just in case something else was missing.

---

