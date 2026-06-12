---
title: "I need Ipod/Amarok help"
date: 2008-09-20
forum: General Help
---

### Post by PrinceArithon on 2008-09-20
Alrighty, I just want to specify that I searched the forum first and found nothing...so I'm asking this stupid question....

Alright I've gotten an Ipod Shuffle to work with Amarok before and there was no problem...but now I'm trying to get my freshly bought Ipod Nano to work with Amarok...and it's not working at all.

First let me tell you some of the weird things.  With the shuffle I got a little Ipod icon, this time I'm getting another icon pop up on the desktop...also I was able to take the shuffle and make it open automatically with Amarok by going to System > Preferences > Removable Drives and Media.  Then after that I'd click on the media tab and I could change it from Rhythm Box to Amarok...there is no multimedia tab in there this time.

OK now down to the real task here.  I got into Amarok configuration and go to add device and I add the ipod selection, but the problem is it starts asking for the name of the ipod, which is fine.  Then it wants a mount point....now in all the tutorials I found on line it didn't say anything about doing all that.  Then when I try to press connect, it wants me to specify the mount point again...and I really have no clue as to how to do that.  It's mounting from a USB that's all I know....so if anyone can let me know what is going on.

Oh I'm using verion 8.04 of Ubuntu...if that helps at all.

---

### Post by gjoellee on 2008-09-20
[http://maketecheasier.com/how-to-sync-amarok-with-ipod-classic-3rd-generation-ipod-nano/2008/03/10](http://maketecheasier.com/how-to-sync-amarok-with-ipod-classic-3rd-generation-ipod-nano/2008/03/10)

:)

---

### Post by PrinceArithon on 2008-09-20
Thank you thank you so much it works.  I appreciate it a lot.

---

### Post by hoverX on 2008-09-26
ok, i tried installing the two packages like the instructions say but i'm getting this error message when i try to install the first one:

trying to overwrite /usr/lib/hal/libgpod-callout which is also in package libgpod-common




Perhaps i don't even need to install this?  i cannot even get Amarok to see my ipod nano as an ipod device.

---

### Post by gjoellee on 2008-09-26
> **hoverX said:**
> ok, i tried installing the two packages like the instructions say but i'm getting this error message when i try to install the first one:

trying to overwrite /usr/lib/hal/libgpod-callout which is also in package libgpod-common




Perhaps i don't even need to install this?  i cannot even get Amarok to see my ipod nano as an ipod device.

Well there are a lot issues with Linux detecting iPods. I cant help you much there, well there is one thing. On your iPod press then center-button and the menu button at once and hold it for a few sec. Then plug it in. That might help:)

---

### Post by hoverX on 2008-09-26
problem solved.  It was the first time using my iPod.  i booted up in Vista (even though it pains me to do so) and transferred some songs over to the iPod.  Now Amarok sees the iPod without any problems whatsoever.

---

