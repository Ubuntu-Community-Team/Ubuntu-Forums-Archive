---
title: "Strange nvidia driver problem, need suggestions"
date: 2008-03-22
forum: Hardware &amp; Laptops
---

### Post by mvidberg on 2008-03-22
I am having a very strange problem with the "nvidia" driver for xorg.  I recently (about 2 weeks) installed ubuntu and everything was working fine, the nvidia module loaded and my 3D games (tremulous, secondlife, UT2004, etc) would run fine... then the other day I rebooted and Xorg didn't come back up.  The moment xorg starts to load it just hard freezes the entire computer (can't do Ctrl-Alt-Delete or Ctrl-SysReq keys).  I have to log in via recovery mode and change the driver in /etc/X11/xorg.conf to "nv" to be able to get back in.  No error messages posted in /var/log/Xorg.0.log.  Now, it is ok to use the "nv" driver to at least have a usuable computer, but why doesn't "nvidia" work for me anymore?

My computer specs are:
MB = Asus M3A
CPU = AMD Athlon X2 4800+
VC = Asus nVidia 7600GS
LCD = Viewsonic VA2026w (connected via a VGA cable, not DVI)

---

### Post by mvidberg on 2008-03-22
Looking at the last 2 lines in my Xorg log file, I see only...

(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so

As you can see, nothing gets logged after it freezes so the log is no help in this situation.

I tried installed "envy" and letting that get the latest nvidia driver and make the modification to my xorg.conf file.  Same thing.  Complete freeze upon nvidia loading.

Is there a way I can make the kernel or xorg log errors even when it crashes like this?

---

### Post by mvidberg on 2008-06-01
Used a Sabayon Linux boot DVD which has nvidia drivers and it loads fine... full 3D acceleration.  Think I will be staying with Sabayon for a while... it's a slick distro.

---

