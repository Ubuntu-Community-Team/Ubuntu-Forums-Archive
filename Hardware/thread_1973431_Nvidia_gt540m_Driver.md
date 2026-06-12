---
title: "Nvidia gt540m Driver"
date: 2012-05-04
forum: Hardware
---

### Post by icedice on 2012-05-04
I just got my new Asus a53s laptop two days ago and of installed ubuntu 12.04 because I knew it would work with my wireless card right out of the box (I usually use 10.04). It works fine with my wireless card but installing my graphics driver is a pain, I always get an error saying that Nouveau kernel drivers are installed. Nvidias help document said to black list the driver and I did that and reboot. However, I continue to get the same error its really starting to **** me off I just want to use my laptop... Anyone know how to remove Nouveau? I have already un-installed it and everything.

---

### Post by Axxon95 on 2012-05-04
Hey, if your GPU is supported, this may help you. It's a copy-paste from a video of mine.

> 1st: Open Terminal and run "sudo add-apt-repository ppa:ubuntu-x-swat/x-updates"

2nd: Then run: "sudo apt-get purge nvidia*"
(to remove any unneeded nvidia packages that could interfere with the setup)

3rd: After that in the terminal type:
"sudo apt-get update"
then
"sudo apt-get install nvidia-current"

4th:  After it downloads the latest drivers and installs them, go to your  Update Manager, refresh updates and get any Ubuntu-X team updates(then  run "sudo nvidia-xconfig"), then restart.
If followed correctly your NVIDIA drivers should work perfectly.Hope it helps.

---

### Post by kwon25 on 2013-04-04
> **Axxon95 said:**
> Hey, if your GPU is supported, this may help you. It's a copy-paste from a video of mine.

Hope it helps.

HI,

I followed the steps precisely and eventually when I restarted the only resolution available is 800x600 and I can not see top menus or sidebars. I am newbie with Ubuntu so not sure what do I need to do to restore my previous settings?

Thank you in advance.

---

