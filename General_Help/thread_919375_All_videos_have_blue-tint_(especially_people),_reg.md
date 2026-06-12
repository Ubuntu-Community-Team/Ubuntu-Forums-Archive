---
title: "All videos have blue-tint (especially people), regardless of playback software"
date: 2008-09-13
forum: General Help
---

### Post by Codename46 on 2008-09-13
Hey guys,

This problem occurred yesterday. When I open a video file using Totem/GXine/VLC/etc. there is a bluish tint in the skin color of people. I was wondering what exactly the problem is and how do i fix it?

I'm running Ubuntu 8.04, my system specs are:

AMD Athlon X2 5600+
2GB DDR800 RAM
Geforce 8800GT 512mb

Thanks.

ETA: When I set Hue to maximum this fixes it, but if I reset it to "default" it looks bluish again.

ETA #2: Changing video output in gstreamer-properties to  "ffmpegcolorspace ! video/x-raw-yuv,format=(fourcc)YV12 ! xvimagesink" doesn't work.

---

### Post by mb_webguy on 2008-09-13
I had this problem a while back, but I don't remember how I fixed it.  If I remember I'll post back...

Just out of curiosity, if you restart X with Crtl-Alt-Backspace, does it help any?

---

### Post by Codename46 on 2008-09-13
> **mb_webguy said:**
> I had this problem a while back, but I don't remember how I fixed it.  If I remember I'll post back...

Just out of curiosity, if you restart X with Crtl-Alt-Backspace, does it help any?

Well the issue has been "fixed" by setting hue to maximum and ctrl-alt-backspace doesn't revert it back.

It would be nice that default settings wouldn't mess it up though :(

---

### Post by Codename46 on 2008-09-14
Bump. Everytime i restart the hue is set a little off of max settings which screws up my color.

Help?

---

### Post by Rainstride on 2008-09-14
> **Codename46 said:**
> Bump. Everytime i restart the hue is set a little off of max settings which screws up my color.

Help?

this happen to me twice in the pass both times was from the codecs, something about the order or mix of codecs caused it. i reinstalled and then used the ubuntu restricted extras instead of choosing the separate codecs. i never get it with the restricted extras for some reason.

---

### Post by Codename46 on 2008-09-14
> **Rainstride said:**
> this happen to me twice in the pass both times was from the codecs, something about the order or mix of codecs caused it. i reinstalled and then used the ubuntu restricted extras instead of choosing the separate codecs. i never get it with the restricted extras for some reason.

What do I do to change my settings so that the restricted extras are used?

If I can find each separate codec and uninstall them then that's just as good as reinstalling right? Because I'm not too keen on reformatting and reinstalling considering how much work it involves

---

### Post by Rainstride on 2008-09-14
> **Codename46 said:**
> What do I do to change my settings so that the restricted extras are used?

If I can find each separate codec and uninstall them then that's just as good as reinstalling right? Because I'm not too keen on reformatting and reinstalling considering how much work it involves

if you go to add/remove and uncheck all the gstreamer plugins and uninstall them first then go back into add/remove and select ubuntu restricted extras it should fix it just so long as its something with the codecs them selves.

make sure you uninstall the plugins then install the restricted extra separately it might screw up if you don't.

otherwise reformatting is the only way i know.:(

---

