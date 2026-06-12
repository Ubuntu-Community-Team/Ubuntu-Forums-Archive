---
title: "Problem with playing songs on new 8.10"
date: 2008-11-18
forum: General Help
---

### Post by firedevilbg on 2008-11-18
Hi, I have a problem with new Ubuntu 8.10 and playing songs with Rhythmbox!
Rhythmbox spontaneously stops to play the song and after 3-4 sec. it continue.
Please help because it's very annoying !

---

### Post by deadowl on 2008-11-18
This is solved for me when I remove the gstreamer0.10-plugins-ugly package

Then, however, if you're using only the ffmpeg codecs, you may still have the problem of not being able to skip forwards/back in Rhythmbox. In addition you'd not be able to play certain file formats (Ex. Windows Media formats).

I haven't tried this, but you might: Try removing gstreamer0.10-ffmpeg and the ugly plugins and download from the Medibuntu repository rather than using the codecs that Ubuntu offers.

You could also try buying the fluendo codecs:
[http://shop.canonical.com/index.php?cPath=19](http://shop.canonical.com/index.php?cPath=19)

---

