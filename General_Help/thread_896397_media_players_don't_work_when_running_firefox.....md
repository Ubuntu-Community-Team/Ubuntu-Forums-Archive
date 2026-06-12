---
title: "media players don't work when running firefox...."
date: 2008-08-21
forum: General Help
---

### Post by ichundu on 2008-08-21
hi,

when i open youtube or any other site that plays video and music, i am not able any more to play my mp3s and other media with rythmbox, movie player, or even vlc. i have to quit firefox to be able use these media players, i can't use them simultaneously. does it happen because of the vlc-mozilla plugin? or is it a driver issue?

i'm wondering if any one can help me solve this.

thanks for your time!

---

### Post by mb_webguy on 2008-08-21
It's the Flash plugin, which has some conflicts with PulseAudio.  Click on the "Installing Flash 10 on Hardy Heron" link in my signature and follow the instructions there to install Flash 10, which fixes the problem.

Alternatively, you could install the libflashsupport package, but it's really only a band-aid solution...

---

### Post by qstraza on 2008-08-21
I think you need some sort of sound server, i may be mistaken tough.

---

### Post by ichundu on 2008-08-21
> **mb_webguy said:**
> It's the Flash plugin, which has some conflicts with PulseAudio.  Click on the "Installing Flash 10 on Hardy Heron" link in my signature and follow the instructions there to install Flash 10, which fixes the problem.

Alternatively, you could install the libflashsupport package, but it's really only a band-aid solution...

i did install flash 10, according to your instructions, but the problem is still there. anyway thanks for the post :)

---

### Post by xouns on 2008-08-21
It's a problem with pulse audio, probably. try [this]("http://ubuntuforums.org/showthread.php?t=866965&highlight=pulse+audio") link.

---

### Post by ichundu on 2008-08-21
i finally solved it. i followed this guide [http://www.uburocks.com/2008/08/18/flash-is-fixed-in-ubuntu/]("http://www.uburocks.com/2008/08/18/flash-is-fixed-in-ubuntu/")

thanks guys for your replies :guitar:

---

