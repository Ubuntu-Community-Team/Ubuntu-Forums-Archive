---
title: "xubuntu edgy: screen resolution and kernel version?"
date: 2006-11-10
forum: Hardware &amp; Laptops
---

### Post by eeried on 2006-11-10
Hello,

I installed Xubuntu Edgy from the alternate CD (text mode installer) on top of my broken Debian Etch+Sid and next to Xubuntu Dapper.

This new install has helped me understand an issue with my Debian Etc+Sid where after an upgrade I couldn't make X work: all I got were "out of scan range" or "no screen" messages!

I have a small screen (false 15")  but it's very good (Trinitron Sony 110ES) and an old outdated but very good video card (Matrox G200 AGP) so the screen can be set at a very high resolution: up to 1284x1024.

Now I usually set the screen resolution to 1024x768: I think it uses less resources than if using a higher resolution (the font size is okay without tweaking).

With Xubuntu Edgy, using this 1024x768 resolution from Xfce settings results in a black screen displaying this message: out of scan range (whatever refresh rate I use). The only resolutions I can use are higher: 1152x864 and the default which seems to be 1284x1024 (fonts look smaller than with 1152x864). the xorg.conf file shows a depth of 24 and the whole series of resolution up to 1284x1024.

 I get a lower refresh rate with these two very high resolution and in one of the two the image is unsteady (probably because the refresh rate isn't high enough).

So what I now understand (perhaps wrongly, please correct me) is that the new kernel no longer accepts my old 1024x768 resolution which worked from kernel 2.4.x to the one used by Dapper (2.6.15.x).

Finally, nobody was able to help me solve my out of scan error in Debian but I think Xubuntu Edgy did! Good work Edgy! In Debian, I had to edit the xorg.conf file and of course as I didn't understand where the problem came from I didn't know how to edit it and reconfigure didn't do the job either.

Do you agree my screen resolution little problem is a kernel thing, and is there any solution if I want to use 1024x768 other than stick with Dapper or any Linux distro based on kernel 2.6.15?

OT: Edgy seems to have launched while it wasn't really ready (but updates will fix that I suppose) and Xubuntu Edgy seems to be heavier than Xubuntu Dapper.

---

### Post by dermotti on 2006-11-10
Hmm i doubt it had anything to do with the kernel.

Any time I have video errors is run this good ole command.

sudo dpkg-reconfigure xserver-xorg

And if usually fixes my issues :-)

---

### Post by eeried on 2006-11-12
[QUOTE][Hmm i doubt it had anything to do with the kernel.

Any time I have video errors is run this good ole command:```
sudo dpkg-reconfigure xserver-xorg
```/QUOTE]

Well, in the case of my stubborn Debian xserver-xorg it didn't work like this. It would have worked if I had set the right resolution, but I couldn't guess I had to choose such a high one for such a small screen as mine!

Now I set the resolution at 1152x864 in **Xubuntu Dapper** and it seems all right. 

So if this resolution change isn't anything to do with the kernel version, could it have something to do with the latest version of xserver?

The mystery thickens ;-)

---

