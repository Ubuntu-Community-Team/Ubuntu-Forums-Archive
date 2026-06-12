---
title: "I really messed up and need help repartitioning."
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by karasuman on 2009-05-11
I have the Acer Aspire One netbook which comes with Windows XP, and, naturally, I wanted to put ubuntu on it instead.  First, I tried the linux4one install, but I didn't like it, so I decided that I'd rather use the ubuntu netbook remix.  This is where I start having problems.

I created the bootable usb drive, chose to boot from it, etc., and the first stages of setup go fine.  Then I get to the "prepare disk space" stage of setup.  When I installed linux4one, I allocated 25% of my hard drive to XP and the remaining to linux4one.  What setup is showing now is the following:

Windows NT/2000/XP (/dev/sda1) 5.9 GB
XP Home (/dev/sda2) 35.3 GB
Ubuntu 8.04.2 (/dev/sda5) 105.1 GB  (this is linux4one)
/dev/sda6 2.9 GB

I have the following three options:
install side by side,
use the entire disc, 
specify partitions manually.

I don't want to use the entire disc because I would like to keep XP.  Installing side by side and dragging the bar to reallocate the space (reducing the room linux4one takes up) gives me an error:

"An error occurred while writing the changes to the storage devices.  The resize operation has been aborted."

I tried to specify the partitions manually, but it says I haven't set up a root file system, so clearly I don't know what I'm doing.  :-/

What I would like to do is delete everything but Windows XP, let it keep the space it has, and use the rest to install the netbook remix.  Can anyone help me?

---

### Post by Miljet on 2009-05-11
You were on the right track using specify partitions manually. You just need to tell the installer to use sda5 for the "/" (root) partition.

Just highlight the sda5 partition and look for an option to select /.

---

### Post by karasuman on 2009-05-11
Thanks, that did it!

---

