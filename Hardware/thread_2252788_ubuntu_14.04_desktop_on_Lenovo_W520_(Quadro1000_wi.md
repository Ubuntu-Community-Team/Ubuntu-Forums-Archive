---
title: "ubuntu 14.04 desktop on Lenovo W520 (Quadro1000 with discrete Graphics dosn't boot"
date: 2014-11-14
forum: Hardware
---

### Post by Roberto_Attias on 2014-11-14
Hello,
I have a Lenovo W520 laptop, which has a NVidia Quadro 100M (Optimus). My goal is to install Ubuntu 14.04 LTS Desktop and the cuda toolset that can be installed here:
[http://developer.download.nvidia.com/compute/cuda/6_5/rel/installers/cuda_6.5.14_linux_64.run](http://developer.download.nvidia.com/compute/cuda/6_5/rel/installers/cuda_6.5.14_linux_64.run).

At first I installed Ubuntu with the default BIOS configuration, and the Nvidia tools after. I was running into issues where Unity will get stuck somewhere: the desktop screen will appear, and I can log in, but after that the desktop screen remains empty. I can ctrl+ALT+F2 to a console, and even start X programs that will show up on the desktop, but without window managers. 

I opened a case with NVIDIA, and they indicated I should set my graphics to Discrete in the BIOS. I also found the same answer in many postings by people. When I tried that however, ubuntu never boots. I tried booting in recovery mode, and the last message shown on the console is:

ACPI: Video device [VID1] (multi-head: yes rom: yes post: no)

If I go back to the BIOS and re-enabled the Optimus mode Linux boots fine. 

I even tried re-installing ubuntu from scratch after setting the BIOS to Discrete, but get the same result: the boot gets stuck after that message.

Can somebody help me with this?

Thanks!

---

### Post by ajgreeny on 2014-11-14
Have you installed **bumblebee** which I hear is getting better?
See [http://askubuntu.com/questions/452556/how-to-set-up-nvidia-optimus-bumblebee-in-14-04](http://askubuntu.com/questions/452556/how-to-set-up-nvidia-optimus-bumblebee-in-14-04)

---

### Post by neuweiler on 2014-12-01
Same problem here with a W530. I already spent hours to find a solution. The only way I can get the system started is to choose "recovery mode" in the grub menu, edit the start parameters by pressing "e" and remove the video related stuff at the beginning (1 or 2 lines). But also then every 2nd attempt, the system freezes - that's certainly not the way to go.

Thanks for mentioning your re-install attempt because that would have been my next act of despair. Did you install 32bit or 64bit kernel/drivers?
My assumption is that because of different devices present on the pci bus, another driver is being loaded. Probably it's a 64-bit driver in initrd. How could we help to debug the problem?

The problem with the empty desktop is a unity/compiz bug. It's a corrupted config file in one of the hidden .config .gconf or .local directories. Don't remember which one. If you don't care about your previous settings, just rename your home directory (e.g. from /home/user to /home/user.old) in the console and then login. Then you'll get a clean desktop and can transfer the original files one by one from the old directory (see also [http://askubuntu.com/questions/249319/my-desktop-is-empty-i-can-only-see-the-wallpaper-how-can-i-fix-it](http://askubuntu.com/questions/249319/my-desktop-is-empty-i-can-only-see-the-wallpaper-how-can-i-fix-it) or [http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears](http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears) )

---

### Post by neuweiler on 2014-12-01
there appears to be a solution for this (although with a non-ubuntu kernel) : [https://devtalk.nvidia.com/default/topic/567297/linux-3-10-driver-crash/?offset=98](https://devtalk.nvidia.com/default/topic/567297/linux-3-10-driver-crash/?offset=98) and also [http://forum.ubuntuusers.de/topic/nach-neustart-kein-login-screen-mehr/](http://forum.ubuntuusers.de/topic/nach-neustart-kein-login-screen-mehr/) mentions a solution in the latest post. Will give it a try.

Edit: According to [findings in the first thread]("https://devtalk.nvidia.com/default/topic/567297/linux/linux-3-10-driver-crash/13/"), it's not a nvidia driver problem but acpi/osl. There's a patch available on [https://github.com/koct9i/linux/commit/a1af2b6c4ab176f1cba95b035e08edb688e1827a](https://github.com/koct9i/linux/commit/a1af2b6c4ab176f1cba95b035e08edb688e1827a) which is scheduled to appear in the kernel 3.19.

---

### Post by neuweiler on 2014-12-01
Hooray, got it working !! (Sorry, one more post.. but the last one.. :) )

Instead of waiting for kernel 3.19, do the following: "sudo apt-get install nvidia-331-update" to replace the older version (likely 304). Then go to the BIOS Display Settings, select "NVIDIA Optimus" and enable OS detection of Optimus. This will result in a boot with intel / LVDS only. But it allows you to use "prime" to switch between using Intel and Nvidia. Start nvidia-settings and go to Tab "Prime" to switch to NVIDIA, logout and back in again. This will result in the same as expected from BIOS setting "Discrete graphics" --> a desktop on a external monitor with NVIDIA and 3D accel. :)
With a dual monitor set-up the desktop was streched and the mouse and windows did not correlate. So I switched to "mirrored" display because that's what I want. I'm sure if you have this issue, it's solvable with xorg.conf adjustments.

To fix the empty desktop problem, I fond another hint: "apt-get install unity-tweak-tool" and then "unity-tweak-tool --reset-unity" wait until it settled, then kill it and reboot. (probably you also need to delete .config/compiz-1 and then use ccsm to enable the unity plugin again).

---

