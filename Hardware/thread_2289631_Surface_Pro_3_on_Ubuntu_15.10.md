---
title: "Surface Pro 3 on Ubuntu 15.10"
date: 2015-08-05
forum: Hardware
---

### Post by aaron103 on 2015-08-05
I have installed Ubuntu 15.10 on my surface pro 3 tablet, the issue is that I have read various places and they all say the the Linux kernal past 3.19 will automatically support the keyboard cover. However with my device this is not the case, I have tried 15.04 and Ubuntu Gnome but to no avail, I was just wondering what you guys think about the issue scene this is reported to be solved by the 3.19 kernel.

Thanks in advance.

---

### Post by Mark Phelps on 2015-08-05
> I have installed Ubuntu 15.10 on my surface pro 3 tabletWhy? At this stage, 15.10 just passed alpha 2 the end of July -- NOT something you should be messing around with, especially on a tablet.  You should wait at least until the Beta release, which is August 27th, before installing this.

You might check in the Development forum to see if anyone there has any advice.

---

### Post by aaron103 on 2015-08-05
I have used Ubuntu 15.04 as well, 15.10 is just what I have on at the moment. I switched to 15.10 to see if the kernel update is what caused the issue. the same exact thing occurred with 15.04 installed as well.

---

### Post by matt082606 on 2015-09-16
I have successfully installed Xubuntu 15.04 on my surface pro 3 with a patched and compiled 4.1.6 kernel. There were a few things I had to do special, like virtualbox had to add 5.0 repository because pre 5.0 version dkms didn't work for the new kernel. 
It is working perfectly for the type cover I have and the patch I used for that should also work for the newest 2 type covers. It also works with the dock, though I occasionally have to restart the ethernet port but once it is working it works for the remainder of the time I am docked, this is just on boot up.

I am happy to share my kernel debs if anyone would like.

I do not dual boot, this was a clean install, but I imagine the kernel will work on a dual boot as well.

Edit:
Anyway the main thing I am here looking for is not related to functionality on the sp3, but I would like to have buttons and apps zoom to 150% by default like they do in Win8/8.1/10 on the sp3

Anyone know a quick way to achieve this?

Also - here are links to the kernel I used, the patches I used, and the compiled debs made on the sp3 - If you install xubuntu (or probably any ubuntu) on the sp3 and then install the kernel and header files below you should be fully operational. I would be curious for those with a type cover other than 07dc.

Kernel - [http://www.mediafire.com/download/6uaz1xaq9nungic/linux-4.1.6.tar.xz](http://www.mediafire.com/download/6uaz1xaq9nungic/linux-4.1.6.tar.xz)
Patches - [http://www.mediafire.com/download/5fy8dn9gp3j39et/kernel-patches.tar.gz](http://www.mediafire.com/download/5fy8dn9gp3j39et/kernel-patches.tar.gz)
compiled - [http://www.mediafire.com/download/rve494xtj688j1b/linux-image-4.1.6-mysurface3-v2_4.1.6-mysurface3-v2-10.00.Custom_amd64.deb](http://www.mediafire.com/download/rve494xtj688j1b/linux-image-4.1.6-mysurface3-v2_4.1.6-mysurface3-v2-10.00.Custom_amd64.deb)
compiled - [http://www.mediafire.com/download/6o41l7peqev4d06/linux-headers-4.1.6-mysurface3-v2_4.1.6-mysurface3-v2-10.00.Custom_amd64.deb](http://www.mediafire.com/download/6o41l7peqev4d06/linux-headers-4.1.6-mysurface3-v2_4.1.6-mysurface3-v2-10.00.Custom_amd64.deb)

You'll need to install both the last two.

---

