---
title: "Ubuntu 10.04 + Nvidia 7600GS"
date: 2010-09-01
forum: Hardware
---

### Post by Clinic on 2010-09-01
First up, this is the first time I've used a linux distro and I've gone with it on a secondary (spare) computer to learn about it as I'll shortly be using it as the OS for my new HTPC. So go easy on me if I don't understand the first time.
 
Basically, I need a bit of guidance; I'm really struggling with this distro/card combination. I can get the nvidia binary drivers drivers to install fine but once I reboot to complete the installation the gnome GUI goes to some insane resolution (like 32x40) and I can't see anything but the top left hand corner of an open window/application and thus, can't change any of the x server settings using the nvidia settings GUI. This of course, makes the GUI unuseable for anything. It's a fresh Ubuntu install on a new HDD.
 
To try and resolve to problem:
[LIST]
[*]I've followed the instructions on [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) and have got no-where.
[*]I've installed nvidia-current drivers from both jockey and the command line.
[*]I've installed nvidia drivers with and without purging nouvea.
[*]I've edited the xorg.conf from the command line using instructions here [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973) (including inputting the monitor's refresh rates and adding the modeline)
[*]I've read forums and googled ubuntu nvidia drivers until I'm blue in the face. Card appears in both the compatibility and incompatabilty lists but last entries are circa 2008.
[/LIST]Monitor is a Viewsonic VX2235wm 22" Widescreen.
 
So, I'm totally out of ideas to fix it, anyone have any ideas? Anyone running this combination can post up their xorg.conf so I can compare? Am I missing something obvious?

---

### Post by an0dos on 2010-09-01
Did you try disabling KMS? If not google "Ubuntu 10.04 nomodeset".
You can also try blacklisting some of the drivers mentioned here: [http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

Delete your xorg.conf and rerun nvidia-xconfig and nvidia-settings.

After you make these changes, deactivate and reactivate the nvidia driver then restart the computer.

---

