---
title: "CPU stutters every 8 to 15 seconds or so"
date: 2010-03-04
forum: Hardware
---

### Post by dusdus on 2010-03-04
Hi there,

First I thought it had something to do with my video driver, because the video playback stutters every 8 to 15 seconds or so. 
But, when I open Kate and press and hold one key, it'll actually do the same: my whole desktop stutters.

I'm using KDE 4.4, so maybe it has something to do with that. I can't find anything in the logs, it's not being filled with some error every 8 to 15 seconds.

I just don't know where to start looking. Anyone?

---

### Post by mikewhatever on 2010-03-04
If you want help, why not reveal more info about your setup? Perhaps I am being presumptuous, but those helping you would most likely want to know what OS version you are running and on what hardware, and there is not a shred of that in your post.
Best of luck.;)

---

### Post by efflandt on 2010-03-05
It would be nearly impossible for anyone to guess without knowing what hardware.  I have an old Compaq V2000 laptop I got when I bought someone a newer computer.  And it seems to have intermittent mousepad lag and lack of keyboard input at times, especially for awhile after booting (Ubuntu 9.10).

At least for gui login I can see if a key registers, because it shows a dot for each password character, so I can tell if I need to hit a key again.  But that is awkward for sudo, which shows no feedback during password entry.

Activating a modem driver for it seemed to help.  But sometimes that can interfere with sound because a winmodem is technically a sound device.  Sound worked in this case, even though both sound and modem are AC'97 devices.  Athough, both devices throw out errors about codecs if I attempt to suspend (which will not successfully resume).

---

### Post by dusdus on 2010-03-06
First of all, thanks for your replies.
The reason I didn't provide too much info is because I felt I only needed some suggestions, not ready made solutions. I had this feeling I missed something in my research. I apparently did not make this clear, sorry about that.

I found the solution btw. Someone pointed out he had similar issues while using the PhotoFrame widget, can't recall the exact name atm. It's the plasma widger which shows a picture at set every interval. 

I don't use the widget, but I recently have set my wallpaper to do the same (Slideshow). I got another wallpaper every 2 minutes. The hicups were every 15 seconds or so, but after disabeling this feature the problem was gone.

I added this information to the bug report of KDE4.4 which the other guy had opened.

So, problem solved and I hope this will help other people as well!

---

