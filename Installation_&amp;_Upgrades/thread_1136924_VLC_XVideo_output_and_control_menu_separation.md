---
title: "VLC XVideo output and control menu separation"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Femaq on 2009-04-25
I have upgraded to Jaunty yesterday and I found out that I've problem controlling videos on full screen under VLC because **control menu have separated from Video window** (XVideo output). 
I've been unsuccessfully trying to join it...

Does anyone know how to fix it ?

---

### Post by Mcavity on 2009-04-25
nope but I have the same thing. also audio starts skiping after video plays for a bit. Its not cpu related as the cpu has power to spare.

---

### Post by puner on 2009-04-25
I have the same thing :(

---

### Post by Solarisphere on 2009-04-25
Yup, same issue here. At least since there's lots of us with the problem it won't be ignored for long.

---

### Post by bngguy on 2009-04-25
same problem here

---

### Post by Nat90 on 2009-04-26
I don't know why they did that, it's so uncomfortable.
They could have at least added the option.

I'm trying to find the 1.0 beta version to see if they fixed it there but unsuccessfully

---

### Post by oraerk on 2009-04-26
Same problem, upgraded from 8.10 to 9.04. tried fresh install too, with same result. Double checked VLC settings (basic and advanced modes), tried all video output types... no success. Does anyone have any ideas?

---

### Post by von Stalhein on 2009-04-27
Sorry to say "me too!"

Is there somewhere we should all be posting this so that the people that matter know?

---

### Post by bngguy on 2009-04-27
> **von Stalhein said:**
> Sorry to say "me too!"

Is there somewhere we should all be posting this so that the people that matter know?

[http://forum.videolan.org/]("http://forum.videolan.org/")

---

### Post by von Stalhein on 2009-04-28
This chap found a workaround.....

[http://ubuntuforums.org/showpost.php?p=7138708&postcount=6](http://ubuntuforums.org/showpost.php?p=7138708&postcount=6)

---

### Post by alphacrucis2 on 2009-04-28
> **Femaq said:**
> I have upgraded to Jaunty yesterday and I found out that I've problem controlling videos on full screen under VLC because **control menu have separated from Video window** (XVideo output). 
I've been unsuccessfully trying to join it...

Does anyone know how to fix it ?

The VLC devs did this on purpose as playing the vids in the main vlc window was causing intermittent problems. A workaround is to install the VLC v1.0 pre release which resolves the problem. You can get it from Kow's PPA:

[https://launchpad.net/~kow/+archive/ppa](https://launchpad.net/~kow/+archive/ppa)

---

### Post by Nat90 on 2009-04-29
That worked great Von Stalhein!
The Full screen menu still doesn't pop up but the separate screen problem is solved. Thanks!


[B]
Attention Kubuntu / KDE users[/B]: You won't need to do the whole Key File part of the tutorial (neither will you be able to); Adept adds the package immediately, so you can skip this step.

---

### Post by slumbergod on 2009-04-30
Adding the PPA and upgrading to the pre-1.0 release sorted out the missing controls in fullscreen mode but introduced a couple of new issues for me - a drop in picture quality and jerky playback. So I rolled back as the new issues made watching video less enjoyable.

The first two PPAs I tried did not work. One did not give me the controls in fullscreen and the other gave me jerky playback as outlined above.

Then I stumbled across this one and it worked for me:
deb [http://ppa.launchpad.net/medigeek/ppa/ubuntu](http://ppa.launchpad.net/medigeek/ppa/ubuntu) jaunty main

The controls were at the top right of the screen so I edited ~/.config/vlc/vlc-qt-interface.conf to adjust the postion:
[FullScreen]
pos=@Point(320 690)

Now it seems fine - controls in fullscreen, no jerky playback, and no loss of picture quality.

---

### Post by bngguy on 2009-04-30
well i downloaded the source code and built ***vlc-1.0.0-pre1 Goldeneye*** , i had to download about 30 different packages, it took me about 45 minutes to download and build the player from scratch,so far i have not had any issues with video and has been working well for me, i would recommend to build the player yourself.

---

### Post by evilGUI on 2009-05-04
I have the same issue, at first I thought something was wrong with my system. I'm using a 8600GT and have the skipping issue when first loading a video, I am using Jaunty at the moment and also get the separate video thing with no full screen controls.

---

### Post by webabun on 2009-05-08
> **slumbergod said:**
> [....]
Then I stumbled across this one and it worked for me:
deb [http://ppa.launchpad.net/medigeek/ppa/ubuntu](http://ppa.launchpad.net/medigeek/ppa/ubuntu) jaunty main

The controls were at the top right of the screen so I edited ~/.config/vlc/vlc-qt-interface.conf to adjust the postion:
[FullScreen]
pos=@Point(320 690)

Now it seems fine - controls in fullscreen, no jerky playback, and no loss of picture quality.

Thanks ! 
Worked fine for me as well. I can enjoy the smooth playback and same quality as with U8.10

---

### Post by infestor on 2009-05-13
(asking as a n00b) how do i add the public key? i couldn't find it

---

### Post by von Stalhein on 2009-05-13
> **infestor said:**
> (asking as a n00b) how do i add the public key? i couldn't find it

Try this: -

[http://ubuntuforums.org/showpost.php?p=7187090&postcount=23](http://ubuntuforums.org/showpost.php?p=7187090&postcount=23)

It explains how that bloke did it anyway.

---

### Post by infestor on 2009-05-13
> **von Stalhein said:**
> Try this: -

[http://ubuntuforums.org/showpost.php?p=7187090&postcount=23](http://ubuntuforums.org/showpost.php?p=7187090&postcount=23)

It explains how that bloke did it anyway.

yeah OK but if that build is lousy i will have to try slumbergod's repository

---

### Post by gywst on 2009-05-30
> **von Stalhein said:**
> Try this: -

[http://ubuntuforums.org/showpost.php?p=7187090&postcount=23](http://ubuntuforums.org/showpost.php?p=7187090&postcount=23)

It explains how that bloke did it anyway.

Thank you all. Any other ways? I don't really want to install this version. I think I'll wait for an official ubuntu version. :(


Thread: [ubuntu] VLC XVideo output and control menu separation

---

### Post by dreadkit.kat on 2009-09-05
Thanks worked for me.Great HOW TO?
Very elaborate Keep up the good work

---

