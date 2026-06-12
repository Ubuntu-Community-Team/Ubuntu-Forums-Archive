---
title: "Dual NVidia 7600GS and 9.04"
date: 2009-05-15
forum: Hardware
---

### Post by brewbie on 2009-05-15
Hello all,

I am in need of serious help, I am a first timer to Ubuntu and started with 9.04. I am currently trying to install my dual nvidia 7600GS drivers in Ubuntu, and every time I get the following "powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor." It seems there is a thread [http://ubuntuforums.org/showthread.php?t=1094316](http://ubuntuforums.org/showthread.php?t=1094316) that was started, but it seems to only happen when I install the drivers for Nvidia. Nvidia seems to want to install [NVIDIA-Linux-x86-180.51.pkg1.run.]("http://us.download.nvidia.com/XFree86/Linux-x86/180.51/NVIDIA-Linux-x86-180.51-pkg1.run")
I did some forum searching and found that I should not use the install "wizard" from within Ubuntu but rather go to TTY1
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-180.51-pkg1.run
sudo shutdown -r now.
I do that and am greeted by the same black screen and error....what am I doing wrong?? I am at the end of my ropes. I tried envy at the suggestion of another poster, but that too is not working...any suggestions on what I am missing, I am sure it is a tiny thing.
Also, I didn't know if this was the right spot to post, I am sorry if it isn't. ):P

---

