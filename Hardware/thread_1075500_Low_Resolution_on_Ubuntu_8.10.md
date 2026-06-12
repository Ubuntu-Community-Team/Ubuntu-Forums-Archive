---
title: "Low Resolution on Ubuntu 8.10"
date: 2009-02-20
forum: Hardware
---

### Post by richorich on 2009-02-20
Hello, i'm newbie in Ubuntu and three days ago i had installed Ubuntu 8.10 (Intrepid Ibex) in my PC (Mb Biostar TF7150U-M7 with onboard VGA NVidia Ge Force 7150/nForce 630i, HDD 40 Gb). After installion, the options for changing monitor resolution is only 800 x 600 and lower (sorry, i forgot).
i had enter Hardware Driver (Systems > Administration) and check the NVIDIA Accelerated Graphic Driver Version 173 (and also Version 177) and activate it. but after restart, i seemed didn't change the graphic resolution.
i also had enter to Ubuntu recovery menu and type :
dkpg-reconfigure xserver-xorg
but it only configure the keyboard instead of the graphic driver.
then i go to Add/Remove Application (Application > Add/Remove..) and i had notice that NVIDIA binary X.org had not been checked (give check mark).i know it need internet connection but (poor me) i had no internet connection in my home. so i download the driver (NVIDIA-Linux--x86-173.14.12-pkg1.run and nvidia-glx-173_173.14.12-1-0ubuntu4_i386.deb) from [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) and [www.packages.ubuntu.com](www.packages.ubuntu.com) using internet cafe and save the driver in my flashdisk. i also had donwloaded Linux kernel 2.6.28.6 (patch-2.6.28.6 in rar files)

What i want is how to install the driver from the flash disk or from local hardisk, configure the graphic resolution (1024 x 786 or higher) and (please) explain the command to install them clearly and correctly.

forgive me if my english is not good.

---

