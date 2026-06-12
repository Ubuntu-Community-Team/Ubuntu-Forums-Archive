---
title: "Graphics Problems With Karmic?"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by KiLaHuRtZ on 2009-11-04
For those having the "flickering" issue with Karmic ... this is a little fix I posted on my website.  Figured I would share with the community. :D

Having problems with Nvidia drivers after upgrading to Karmic? If you cannot get your desktop manager to start with kernel 2.6.31, then this may be you. A quick fix is to just install the most recent (stable) Linux drivers right from [Nvidia]("http://www.nvidia.com/object/unix.html"). First, download the driver that applies to your particular installation and SFTP it to the troubled machine. Next, SSH to the troubled machine and kill your desktop manager (i.e. GDM/KDM/XDM, etc.).

```
sudo /etc/init.d/[GDM|KDM|XDM] stop
```

Locate the file you downloaded from Nvidia and make it executable.

```
sudo chmod 755 /path/to/your/file
```

Now, execute it and follow the on screen instructions.

```
sudo /path/to/your/file
```

For the last option, make sure you answer "YES" so it will use the new Xorg config on the next boot. Last, just reboot and you should be all set! Note, that this process will be required each time you update to a new kernel. However, the benefit here is you can always have the most recent Nvidia drivers! And as always, follow these instructions at your own risk! We will not be held responsible should you screw up your system.

---

