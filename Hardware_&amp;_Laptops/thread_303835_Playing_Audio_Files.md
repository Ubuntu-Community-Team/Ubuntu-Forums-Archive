---
title: "Playing Audio Files"
date: 2006-11-20
forum: Hardware &amp; Laptops
---

### Post by karmon on 2006-11-20
Hey, I've been using Ubuntu 5.10 for a while, haven't seen a need for the update, but one thing that's puzzled me is that I can't play any audio files. In amarok it says that they can't be loaded. My soundcard works, i know this because i can hear audio from videos on sites such as youtube.

---

### Post by tommcd on 2006-11-21
Have you installed the multimedia codecs?
[https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/codecs.html](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/codecs.html)

Those instructions are for Dapper. I think it is gstreamer 0.80 version in breezy.
Also install all the stuff on the restricted formats page:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

You should consider upgrading to Dapper. It is much better than breezy IMO. I always do a clean install though, rather than dist-upgrade. More reliable and less likely to cause problems. Hope this helps.

---

### Post by rlozano on 2006-11-21
> **karmon said:**
> Hey, I've been using Ubuntu 5.10 for a while, haven't seen a need for the update, but one thing that's puzzled me is that I can't play any audio files. In amarok it says that they can't be loaded. My soundcard works, i know this because i can hear audio from videos on sites such as youtube.

you can try and install easyubuntu... it may help you install the codecs that you need automatically. i don't think that automatix still support 5.10

---

