---
title: "Fixing Intel Graphics GLX after Lucid 10.04 upgrade"
date: 2010-05-04
forum: Hardware
---

### Post by Orion36 on 2010-05-04
Hello there:

After looking and looking around I found a way to fix my "segmentation failure" of the glx library.

Thanks to the guy who found it.

Just copy and Ctrl+Shift on console this commands, will reset the intel driver and fix the wrong pointer of the glx library.

sudo apt-get purge nvidia*
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-alternatives --remove gl_conf /usr/lib/nvidia-current/ld.so.conf

PD: my LG500, core duo, intel santa rosa i flying with the "X updates" now.

---

### Post by dtakamori on 2010-05-15
Thanks for your info. Please correct me if I'm wrong, but is the original person who helped you asvravi who listed the solution at post [#10]("http://ubuntuforums.org/showpost.php?p=9212078&postcount=10") on another ubuntuforums thread titled "[**Getting 'Desktop effects could not be enabled' error while  trying to enable 'compiz'.**]("http://ubuntuforums.org/showthread.php?t=1466531")"?  Just want to give props to the original person, if possible.

System: Dell 530n, Intel G35 chip which shipped with previous LTS

Unrelated: Still working on fixing my Dell 700m's hang on boot (I have a workaround and found the related threads already; not asking for help here on that). Argh.

---

