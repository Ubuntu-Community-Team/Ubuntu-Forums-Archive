---
title: "nVidia driver causes low resolution gdm on start"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by Addis on 2007-04-22
I upgraded from a clean install of Edgy to the preview of Feisty. After the distribution upgrade, everything seemed fine.

At that point, I believe I was using the 2.6.20-14-generic kernel, and when the restricted drivers manager installed nvidia-glx for me everthing was great.

Then I ran into a problem when after running updates the kernel was upgraded to 2.6.20-15-generic and also nvidia-glx was upgraded as well. Now every time it starts, the gdm login screen has a hideously low 640x480 resolution. My only solution to this is to press CTRL-ALT-BACKSPACE since there's no option to restart X server from gdm. Once X restarts, the resolution goes back to the nice 1280x1024 I wanted.

Strange thing is it was working fine until some updates ran, and I'm not sure if this is a binary issue or a kernel issue.

---

