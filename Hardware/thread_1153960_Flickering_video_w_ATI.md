---
title: "Flickering video w/ ATI"
date: 2009-05-09
forum: Hardware
---

### Post by geovino on 2009-05-09
I'm running Ubuntu 9.04 on a Acer laptop, w/ ATI video. Everything runs well except some flicking video. I also tried to install Cooliris for Firefox and it barely works at all.

Is there a fix for the flicking video?

---

### Post by Private_Ops on 2009-05-09
Do you have Compiz on? Turn it off. 

Otherwise I have no idea.

---

### Post by hanbin973 on 2009-05-09
From 9.3 driver , there is no flicker in Xv accerloration. And from 9.4 there is no flciker in GL accerloration.

Try to use the latest driver.

---

### Post by 7CarPileUp on 2009-05-10
im having the same issue on 8.10. if your using VLC you can change the X11 through the GUI.  
If your using totem you can press ALT+F2
type gstreamer-properties
Go to the video tab and change it to X window system.

That way you can keep compiz on and not have the flickering.

---

### Post by ssri on 2009-05-10
> **hanbin973 said:**
> From 9.3 driver , there is no flicker in Xv accerloration. And from 9.4 there is no flciker in GL accerloration.

Try to use the latest driver.

Yup, use Catalyst 9.3 for Intrepid and 9.4 for Jaunty.  I think 8.6 is the version included in Intrepid,  where there is video flickering when compositing is enabled.  Download the latest drivers for your distro from ATI and that problem will be gone.  Remember to use the _[ubuntu guide]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide")_ when installing them .

---

### Post by geovino on 2009-05-11
Thanks. The instructions are a bit confusing, so I haven't tried it yet.

This morning I saw this link:
[http://webuflipd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html](http://webuflipd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html)

I added these repos and updated. I still have a occasional flicker, but not much. Maybe another update will correct correct the problem.

---

