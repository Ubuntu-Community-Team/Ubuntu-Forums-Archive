---
title: "Help installing the old Nvidia driver for Presario F500?"
date: 2008-09-09
forum: Hardware
---

### Post by samuraiCat on 2008-09-09
UPDATE!

It worked! I just had to add this to the Devices section of xorg.conf:
Driver "nvidia"

**********************


Good morning. I'm having a lot of problems with Hardy and the  nvidia_glx_new driver on my Compaq Presario F500 series laptop, and I wonder if someone can help out. I tried to follow Xiong Chiamiov's tutorial to use the newest drivers, but these drivers also cause problems on my machine. Here's Xiong's thread: [http://ubuntuforums.org/showthread.php?t=797270&page=12](http://ubuntuforums.org/showthread.php?t=797270&page=12) 

Later, I found out on this Launchpad post that both the 167.x and 172.x Nvidia drivers won't work for my laptop: [https://bugs.launchpad.net/ubuntu/+bug/207749](https://bugs.launchpad.net/ubuntu/+bug/207749) 

That bug report describes the exact problem that I'm having. Apparently, neither the nvidia drivers from the repos or the new ones from Nvidia will work on my machine. I apparently need to use the old Feisty drivers (which worked great, btw).

I followed the instructions that one user posted near the end of the thread, but now I'm hung up on one part. I'm hoping someone can help me with the next step. Here's what I followed (pasted from that Launchpad thread):
> I solved it, installing the latest drivers won't work either....

i have to roll back to the 100.14.19 drivers, these seems to be working fine, no garbled consoles (i don't have a system hangs yet either)

firstly uninistall the ubuntu nvidia driver in the restricted hardware app...

the follow this guide to clean the system( [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490) )[quote]

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"

Additionally, delete the following file if it exists:

    /lib/linux-restricted-modules/.nvidia_new_installed

Now donwload this drivers set ([http://www.nvidia.com/object/linux_display_ia32_100.14.19.html](http://www.nvidia.com/object/linux_display_ia32_100.14.19.html))

go to the console (crtl-alt-f1)

stop gdm
sudo /etc/init.d/gdm stop

go to the driver download folder, and do

sudo sh NVIDIA-Linux-x86-100.14.19-pkg1.run


don't donwload the kernel modules, compile it ... reboot and Voila

another nvidia nightmare solved for me....
[/quote]

I followed these instructions exactly, but the new driver does not appear to be running yet. I thought I screwed it up, but when I followed the instructions a second time, I received a message saying "Driver 100.blah.blah is currently installed. Do you want to reinstall?" I reinstalled anyway, but still nothing.

Here's my question: How do I get this old driver to work? Since this wasn't from the repos, do I need to add "nvida" into my xorg.conf file manually?

---

