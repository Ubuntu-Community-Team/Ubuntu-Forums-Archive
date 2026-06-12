---
title: "Skype icon with dark background"
date: 2008-07-18
forum: General Help
---

### Post by co0lingFir3 on 2008-07-18
Hi folks,
since yesterday my skype icon in the taskbar has a strange dark grey background. Yesterday i enabled the backports repo in the package manager and it updated the following software:
```
evolution-common (2.22.2-0ubuntu2) to 2.22.3.1-0ubuntu1
evolution-data-server (2.22.2-0ubuntu2) to 2.22.3-0ubuntu1
evolution-data-server-common (2.22.2-0ubuntu2) to 2.22.3-0ubuntu1
ffmpeg (3:0.cvs20070307-5ubuntu7+medibuntu1) to 3:0.cvs20070307-5ubuntu7+medibuntu1.1
libavcodec1d (3:0.cvs20070307-5ubuntu7+medibuntu1) to 3:0.cvs20070307-5ubuntu7+medibuntu1.1
libavformat1d (3:0.cvs20070307-5ubuntu7+medibuntu1) to 3:0.cvs20070307-5ubuntu7+medibuntu1.1
libavutil1d (3:0.cvs20070307-5ubuntu7+medibuntu1) to 3:0.cvs20070307-5ubuntu7+medibuntu1.1
libcamel1.2-11 (2.22.2-0ubuntu2) to 2.22.3-0ubuntu1
libebook1.2-9 (2.22.2-0ubuntu2) to 2.22.3-0ubuntu1
libecal1.2-7 (2.22.2-0ubuntu2) to 2.22.3-0ubuntu1
libedata-book1.2-2 (2.22.2-0ubuntu2) to 2.22.3-0ubuntu1
libedata-cal1.2-6 (2.22.2-0ubuntu2) to 2.22.3-0ubuntu1
libedataserver1.2-9 (2.22.2-0ubuntu2) to 2.22.3-0ubuntu1
libedataserverui1.2-8 (2.22.2-0ubuntu2) to 2.22.3-0ubuntu1
libegroupwise1.2-13 (2.22.2-0ubuntu2) to 2.22.3-0ubuntu1
libexchange-storage1.2-3 (2.22.2-0ubuntu2) to 2.22.3-0ubuntu1
libgdata-google1.2-1 (2.22.2-0ubuntu2) to 2.22.3-0ubuntu1
libgdata1.2-1 (2.22.2-0ubuntu2) to 2.22.3-0ubuntu1
libpango1.0-0 (1.20.1-1) to 1.20.5-0ubuntu1
libpango1.0-common (1.20.1-1) to 1.20.5-0ubuntu1
libpostproc1d (3:0.cvs20070307-5ubuntu7+medibuntu1) to 3:0.cvs20070307-5ubuntu7+medibuntu1.1
libswscale1d (3:0.cvs20070307-5ubuntu7+medibuntu1) to 3:0.cvs20070307-5ubuntu7+medibuntu1.1
```
I dont know if it has something to do with updating but i thought it might be helpful.
Here is a screenshot of my problem:
[IMG]http://jul18.imghost.us/Mrcd.png[/IMG]

PS: I have compiz enabled an I'm using a transparent task-bar.

Greets,
co0lingFir3

---

### Post by danhm on 2008-07-18
That seems to be a bug in Skype, I think. Mine tends to become the icon the right of it.

---

### Post by co0lingFir3 on 2008-07-20
But it's strange that this bug only occured since some days... Now e.g. the background is darker than yesterday... nearly black.
Afair there were no updates for skype in the last few days.
What do you mean with "to become the icon the right of it"?

---

### Post by Tryfon on 2008-10-14
Mine too. For example right now the skype icon is actually a skype icon over an aMSN icon (the real aMSN icon lies just next to it). It's weird, it has to be a skype's bug. Anyone who has an idea how to fix this please enlight us.

---

### Post by lelamal on 2008-11-25
> **Tryfon said:**
> Mine too. For example right now the skype icon is actually a skype icon over an aMSN icon (the real aMSN icon lies just next to it). It's weird, it has to be a skype's bug. Anyone who has an idea how to fix this please enlight us.

My problem is the other way around: I normally get a black box with the aMSN tray icon on top, behind which I can also guess previous statuses or login stages, as if the background didn't get refreshed properly.

After bumping into this thread, I learnt this might be connected with Skype (although I have never had any problem with its icon) and tried the following: I switched both apps off, then started only aMSN. The result was what Tryfon described, but the other way around, i.e. an aMSN icon over a Skype icon, although the latter was actually off. When finally turned on, nothing much happened apart from the normal Skype icon sitting next to the overlapping icons just described.

Thanks in advance for any tip on how to solve this bug.


UPDATE:
After following the exchange at [this link]("http://forum.eeepc.it/viewtopic.php?id=7479") I finally found a good workaround. The two guys are actually suggesting to change skin, which I did. After trying many, I am now using the one called *Tux*, and the tray icon finally redraws correctly every time aMSN changes status, or the icon moves when other icons replace it on the panel. Among those I tried, this is the only skin that worked for me (actually, I love the little penguin sitting on my panel), but your experience might differ. Enjoy!

---

