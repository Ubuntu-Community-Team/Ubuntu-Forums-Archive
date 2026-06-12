---
title: "tablet PC compatibility"
date: 2011-12-04
forum: Hardware
---

### Post by xtgyal on 2011-12-04
Is Ubuntu Desktop compatible with tablet PCs?  Specifically, a hybrid (can be used as a laptop or tablet) HP tx2525nr 64-bit multimedia tablet?.  Hardware compatibility I'm worried about include: the active stylus (which can draw or write when pressed on the screen, but like a pencil, the opposite end is used to erase or delete, can also move the mouse cursor when in tablet mode by placing in proximity to the screen, and has both right- and left-click functionality), integrated webcam and dual microphones (for stereo recognition of incoming sound direction), hotkeys for rotating the screen in tablet mode (up, down, left, right), and the LightScribe drive for burning text or images onto CDs/DVDs.  I also need text-to-speech, speech-to-text, and handwriting-to-text capability (e.g. to run something along the lines of the MS OneNote engine, or MS OneNote itself in Wine, but also to be able to input text via the stylus on any application).  Voice control would be preferable as well for hands-free use.  The computer also has an IR remote control for multimedia/TV and a multicard reader.

---

### Post by Favux on 2011-12-04
Hi xtgyal,

That's quite a list.  But yes you can set up a HP TX2500 and get most everything working.  Two of the four bezel buttons we've never got working though, but you should be able to bind one of the two working ones to a rotation script.

The Wacom digitizer is no problem, should work out of the box.  Magick Rotation will work fine for automatic rotation.  CellWriter for letter-to-text.  OneNote type handwriting-to-text isn't really available yet, although there is a workaround.  Xournal for notes and PDF annotation.  Speech I don't know for sure, but I think I've seen stuff on that.  I thought the TX2500 only had one microphone.  LightScribe is proprietary and I don't think there is a linux equivalent (last time I checked) but using the DVD drive to burn disks is supported and easy.  Just no LightScribe labels.  I burn those in Windows.

[http://ubuntuforums.org/showthread.php?t=845911](http://ubuntuforums.org/showthread.php?t=845911)
[http://ubuntuforums.org/showpost.php?p=6274392&postcount=1](http://ubuntuforums.org/showpost.php?p=6274392&postcount=1)
[https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

---

