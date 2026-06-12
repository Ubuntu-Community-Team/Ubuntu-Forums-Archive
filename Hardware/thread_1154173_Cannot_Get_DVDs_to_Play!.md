---
title: "Cannot Get DVDs to Play!"
date: 2009-05-09
forum: Hardware
---

### Post by dwieeb on 2009-05-09
I had it working in Ubuntu 9.04 when I had that installed on my eeePC. I decided to install UNR but that ended up causing even more problems. For example, nothing I try will play a DVD. I have libdvdread4 and libdvdnav4. I have tried Movie Player, Movie Player (xine) and even VLC but none of them work. Movie Player just sits and thinks for a long time and does nothing. Movie Player (xine) gives me this message: "The source seems encrypted and can't be read. Are you trying to play an encrypted DVD without libdvdcss?" Which appears to be an outdated error message. VLC gives no error but it simply won't play the DVD. Am I missing any codecs? What's going on?

---

### Post by whistlingtony on 2009-05-09
Ahh.... 

Well, that's not such an outdated error message.

Most DVD disks are encrypted to stop evil pirates(Doesn't work mind you, and is pain in everyone elses bum). Most folks don't realize that, as DVD players unencrypt everything on the fly, and most computers that you buy have legal software to unencrypt everything.

You don't have that software. So, you need to get libdvdcss2, which is illegal in the U.S.A (Yay freedom!), or get some other trick.

Directions to fix your issue can be found at [https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/) or do a google search for "Ubuntu how to play DVD" and you'll have all the answers you need.

Heh, and if you want to be legal about it... there are ways, but I don't know them. :D

-T

---

