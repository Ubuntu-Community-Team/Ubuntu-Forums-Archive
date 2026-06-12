---
title: "Ubuntu really freaking slow on HP dv6113"
date: 2008-10-08
forum: Hardware
---

### Post by erinspice on 2008-10-08
Ubuntu is ridiculously slow on my laptop. It gets better when I reboot, but it goes downhill after that. I moved away from Windows because I had to reboot all the time. I will have no choice but to switch away from Ubuntu if I can't get this resolved.  My laptop is a dual 1.6 Ghz with 1 GB RAM.  The server load spikes up near 4 when things go bad, and my memory is about 10% free (none or little in cache) during those times. I regularly run Pidgin, Thunderbird, FireFox, Picasa, and a gnome terminal at the same time, but that's about it.

A friend mentioned that it could be a driver issue. What do you guys think?  Also, could it have anything to do with the fact that this is a dual processor machine? I know you are capable folks and I really appreciate your help and look forward to getting Ubuntu running smoothly enough that I can continue using it!

---

### Post by cariboo on 2008-10-08
It  wouldn't surprise me that it is a video driver issue. What type of video card does your laptop have. To find out, in a Applications-->Accessories-->Terminal type:

```
sudo lshw -c video
```

and post the output in your next post.

Jim

---

### Post by erinspice on 2008-10-08
I have a Geforce 6150.

---

### Post by abrianb on 2008-10-08
Try System>prefrences>Search and Indexing. then disable indexing and watching. This option has caused me problems in the past. Good luck.

---

### Post by erinspice on 2008-10-08
Thanks, but I'd already disabled those "features."

---

### Post by erinspice on 2008-11-10
Please excuse the shameless bump. It's been four weeks, and I've still made no progress on this.  Does anyone have any ideas why Ubuntu is so slow?

```
erin@erin-laptop:~$ apt-show-versions  | grep -i vid
xserver-xorg-video-s3/hardy uptodate 1:0.5.0-4
xserver-xorg-video-voodoo/hardy uptodate 1:1.1.1-5
xserver-xorg-video-vga/hardy uptodate 1:4.1.0-8
xserver-xorg-video-cirrus/hardy uptodate 1:1.1.0-8ubuntu1
xserver-xorg-video-intel/hardy uptodate 2:2.2.1-1ubuntu13.7
xserver-xorg-video-mga/hardy uptodate 1:1.4.8.dfsg.1-1
xserver-xorg-video-tseng/hardy uptodate 1:1.1.1-4
xserver-xorg-video-ati/hardy uptodate 1:6.8.0-1
xserver-xorg-video-rendition/hardy uptodate 1:4.1.3.dfsg.1-4
xserver-xorg-video-fbdev/hardy uptodate 1:0.3.1-4
xserver-xorg-video-cyrix/hardy uptodate 1:1.1.0-8
xserver-xorg-video-openchrome/hardy uptodate 1:0.2.901-0ubuntu4
xserver-xorg-video-sis/hardy uptodate 1:0.9.3-6
xserver-xorg-video-glint/hardy uptodate 1:1.1.1-8
xserver-xorg-video-vmware/hardy uptodate 1:10.15.2-1ubuntu2
xserver-xorg-video-all/hardy uptodate 1:7.3+10ubuntu10.2
libxvidcore4/hardy uptodate 2:1.1.2-0.1ubuntu3
xserver-xorg-video-dummy/hardy uptodate 1:0.2.0-7
xserver-xorg-video-trident/hardy uptodate 1:1.2.4-1
xserver-xorg-video-savage/hardy uptodate 1:2.1.3-5
xserver-xorg-video-v4l/hardy uptodate 1:0.1.1-6ubuntu1
xserver-xorg-video-neomagic/hardy uptodate 1:1.1.1-8
xserver-xorg-video-sisusb/hardy uptodate 1:0.8.1-9
xserver-xorg-video-vesa/hardy uptodate 1:1.3.0-4ubuntu4
xserver-xorg-video-nv/hardy uptodate 1:2.1.8-1ubuntu1
xserver-xorg-video-s3virge/hardy uptodate 1:1.9.1-7
nvidia-kernel-common/hardy uptodate 20051028+1ubuntu8
xserver-xorg-video-tga/hardy uptodate 1:1.1.0-9ubuntu1
xserver-xorg-video-ark/hardy uptodate 1:0.6.0-9
nvidia-glx-new/hardy upgradeable from 169.12+2.6.24.13-19.45 to 169.12+2.6.24.14-21.51
xserver-xorg-video-i128/hardy uptodate 1:1.2.1-4
xserver-xorg-video-via/hardy uptodate 1:0.2.2-5
xserver-xorg-video-tdfx/hardy uptodate 1:1.3.0-6
xserver-xorg-video-apm/hardy uptodate 1:1.1.1-10
nvidia-settings/hardy uptodate 1.0+20080304-0ubuntu1.1
xserver-xorg-video-i810/hardy uptodate 2:1.7.4-0ubuntu7
xserver-xorg-video-siliconmotion/hardy uptodate 1:1.5.1-3
xserver-xorg-video-chips/hardy uptodate 1:1.1.1-9

```

---

### Post by elTio on 2008-12-05
I got the freaking same problem on my laptop. A dell inspiron 640m.

---

### Post by erinspice on 2008-12-05
I'm almost certain that this is a video driver problem. I've noticed that the more the screen has to update, the faster my system goes downhill.  I'm going to play around with this a little, and if I can't get it fixed, I'm going to have to go back to Fedora.

---

### Post by iggykoopa on 2008-12-05
if you want to see if it's the video drivers you could try changing to the open source nv drivers to test it out. You'll lose 3d excelerration (no compiz) but at least it'll tell you if your headed in the right direction. in your xorg config add in the section that looks like this:
Section "Device"
        Identifier      "Configured Video Device"
EndSection

change it to:
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nv"
EndSection

if it doesn't work or you want to change back just remove the driver line.

---

### Post by erinspice on 2009-05-03
Please excuse the ancient thread bump. I wanted to resolve this thread with the hope that it might help someone else. Passing the kernel the "noapic" option solved all my problems.

---

