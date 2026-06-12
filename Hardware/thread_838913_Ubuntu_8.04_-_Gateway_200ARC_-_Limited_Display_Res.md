---
title: "Ubuntu 8.04 - Gateway 200ARC - Limited Display Resolution - 800x600"
date: 2008-06-23
forum: Hardware
---

### Post by Presbuteros on 2008-06-23
I should first say that I am a new linux user but can be a quick learner. I have installed and updated Ubuntu 8.04 on a Gateway 200ARC laptop. The screen resolution is limited to 800x600. It is capable of a higher resolution when running Windows XP. My hope is that it can run a higher resolution with this version of linux.

After consulting [[COLOR="Red"]this thread[/COLOR] ]("http://ubuntuforums.org/showthread.php?t=570107&highlight=gateway+200arc")I ran the command "lspci" and received this output:

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

Someone suggested that I visit [[COLOR="Red"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=420185&highlight=intel+915+resolution") that discusses a "915 resolution."

In that thread it suggested I run the command "sudo apt-get install xserver-xorg-video-intel." I ran that command and it gave me the following output:

xserver-xorg-video-intel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I am unable to attain a higher resolution. Any help would be greatly appreciated.

---

### Post by Presbuteros on 2008-06-26
Simply fell back to 7.10 but am still eager to know if my graphics can work in 8.04.

---

