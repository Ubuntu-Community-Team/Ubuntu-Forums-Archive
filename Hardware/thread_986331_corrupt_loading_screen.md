---
title: "corrupt loading screen"
date: 2008-11-18
forum: Hardware
---

### Post by newbrain on 2008-11-18
Hi,
I have just installed The Intrepid Ibex on my old hp notebook, eventhing seems to work just dandy..apart from..well thats for another post..my biggest niggle at the moment concerns the ubuntu loading screen. you know the old progress bar below the ubunto logo.

Well, for some reason, I sometimes get corruption. I don't mean snow, or anything like that, but sometimes (and its hard to pin down) I get an image of a second progress bar further up and to the left. I say image cuz I'm guessing that this is a video memory syn problem. anyone else had this? its not fatal, and once loaded eveything seems just fine..but it does grib my gears..

Im a complete newbie btw so please don't send me cryptic responses

Keep up the fight
Steve

p.s.
my notebook is an hpz5000 with an ati radion m9 mobilty processor

---

### Post by ajgreeny on 2008-11-18
Yes, I think I have seen it once in my four or five boots so far into intrepid.  I run hardy mainly at the moment and it is brilliant so have put intrepid on a second disk to look at when I have time.  I have an amd sempron 2400+ on an asus m/b with 1GB ram and an ATI/Radeon 9200SE graphics card (one of the best older Radeon cards,I think, which works well with the OS driver).  Most things on intrepis were OK except the resolution which was set too high for my monitor, the first time ever that has happened, some other distros set it too low, but ubuntu has always got it right in the previous versions.  I solved this by adding the display resolution lines from an older backup of xorg.conf (Dapper, I think) and now all is well with that.

Anyway, to my point;  do you think perhaps the usplash ghostimage we see is a result of an ATI card?

---

### Post by newbrain on 2008-11-18
yes...ive done my bit video driver development back in the day, and my guess is that its an ati driver issue.

---

### Post by newbrain on 2008-11-19
Here is a picture of the kinda think I'm getting

[http://launchpadlibrarian.net/17989328/usplash-doubled-progress-bar.png]("http://launchpadlibrarian.net/17989328/usplash-doubled-progress-bar.png")

Any ideas?

---

