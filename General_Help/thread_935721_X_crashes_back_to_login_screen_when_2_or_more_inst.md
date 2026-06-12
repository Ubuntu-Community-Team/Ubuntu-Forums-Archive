---
title: "X crashes back to login screen when 2 or more instances of some X apps are running"
date: 2008-10-02
forum: General Help
---

### Post by rbpember on 2008-10-02
With several graphically intensive X applications (fortunately, not most!), I've found that my X session crashes back to the login window if I'm running 2 or more instances of these applications. (I'd rather not name the applications because I don't think they are themselves at fault, they come from quite different sources, and I don't want rumors flying around about them that might sully their reputations.) After crashing back to the login window, I am able to log right back in; I don't experience any hanging or lock up.

The crash only happens if two or more of the instances are unminimized, and usually only if I'm doing some sort of mouse/graphics operation, although for one of the programs merely firing up two instances often causes the crash.  The crash is very repeatable. If two instances are unminimized, 
the crash happens within in a minute or less if I'm interacting with the app.

The error does not require gnome: I experiemented with ctrl-alt-f1, and using xinit with twm or even no window manager, and the crash still happens. (In this case, I crash back to the login shell.) 

I think the error has something to do with glx because I captured the output from xinit --  -- and see that the traceback goes through lixglx.so. 
See attached files xinit.out and xinit.3.out. These were dumps from 2 different applications causing the crash.

Some details or my setup: I'm running Gutsy Gibbon (this is my work machine and I haven't had time to safely upgrade yet.) I have a  Dell Precision M6300 laptop with an NVIDIA QUADRO FX1600M. Although the laptop has 64 bit processors, I had trouble getting the 64 bit OS to work, so I'm running the 32 bit OS. Also, I had trouble getting the full Nvidia drivers to run, so I'm not using any proprietary drivers. 

I've had the machine with Gutsy since last November. I don't remember precisely when I started seeing the error. I've been keeping up with the updates, so possibly one of the updates triggered what I'm seeing. The work around has been to keep all but one of the instances minimized. Lately, I've had more need to look at multiple instances at the same time, so it's become much more of a headache.

I'm also attaching my xorg.conf, which is pretty vanilla, and an Xorg.0.log from one of my crashes.

(Attached files are in gzipped tar file rbpember_100108.tar.gz)

---

### Post by rbpember on 2008-10-02
**aha! The error also happens with glxgears -- stupid me for not trying that earlier.**

Other piece of information: I'm using the mesa version of glx, not the Nvidia version.

---

### Post by rbpember on 2008-12-09
I finally had some time to resolve this. It turned out the key was that I was using the Mesa drivers instead of Nvidia drivers. I tried running the unrestricted Nvidia drivers, but received  messages along the lines of my display not being a glx display when attempting to run a glx app. So, I took the path of least resistance, and am now running the restricted Nvidia drivers. (Not the Ubuntu way, I know, :icon_frown: )BTW, there's an excellent discussion on how to use TwinView (which is also Nvidia proprietary) at [http://www.ubuntugeek.com/dual-monitors-with-nvidia.html#comment-157713](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html#comment-157713)

---

