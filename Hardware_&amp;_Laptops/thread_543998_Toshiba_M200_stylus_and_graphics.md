---
title: "Toshiba M200 stylus and graphics"
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by frith on 2007-09-05
Hi there,

I have only made about a dozen forum posts my whole life, so if this come out wrong, sorry in advance.

I fairly recently installed ubuntu feisty on my toshiba m200. It has been a great experience so far - starts up so much quicker than XPtablet, and most things work.

But of course, with me screwing around a couple things are now broken :)

1. I tried (rather stupidly in retrospect) to install the nVidia drivers from the nVidia website using their guide and installer. Now whenever I enable them the X server won't start because the kernel version of the drivers is different to the X kernel version (or something like that...)

I tried doing apt-get remove nvidia-glx nvidia-glx-new and nvidia-glx-legacy, and they removed successfully, but when I reinstall them I still get the same error. How do I wipe these drivers completely and reinstall properly?

Also, the stylus. To my surprise and delight it worked straight up after installing. Now it doesn't and I can't work out why. I did mess about a little too much with my xorg.conf file when I was trying to get dual monitors to work (incidentally I couldn't). I did the rebuild using the sudo dpkg-reconfigure -phigh xserver-xorg command, but it still doesnt work.

I had a little look in the xorg.0.log file and it seems to load the drivers - there are no errors relating to the wacom stuff.

When I do wacdump /dev/input/wacom it says 'no such device'
Oh, and it does work under windows still, so I'm pretty sure its not a hardware problem.

Can anyone shed some light on these issues?

Thanks,

Frith.

---

