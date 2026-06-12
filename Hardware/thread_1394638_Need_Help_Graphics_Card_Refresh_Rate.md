---
title: "Need Help: Graphics Card Refresh Rate"
date: 2010-01-30
forum: Hardware
---

### Post by EmoDx on 2010-01-30
I need help with setting my graphics card refresh rate below 75hz. Just installed Karmic and luvin it so far. My only problem is streaming video. My hardware:

Intel BX Board
Intel 600 Mhz Processor
384 MB Ram
Unknown Graphics Card
Airforce One Wireless
Sony DVD Player

So I already know that the answer is not enough ram or processor. And I can accept that except for these two reasons:

1. If I play a DVD, I get a great picture!
2. I installed Midori and set my Flash video quality to low and got a little better playback.

When I was running Heron back in the day, I could stream a little better. So how do I go about betting my refresh rate lower? I did a search an found a threadthat looked promising but had a dead link. And the other two threads didn't work for me. Can someone turn me onto a thread that will walk me through? Thanks!

---

### Post by Yellow Pasque on 2010-01-30
I'm confused. How does changing your refresh rate improve video playback performance? If you have a CRT monitor, going below 72Hz or so is no good for your eyes. At any rate, you would accomplish this in /etc/X11/xorg.conf

---

### Post by EmoDx on 2010-01-31
Well I am thinking that because it is an older graphics card that the card is off-loading some of the functions to the main processor. Because the video is delivered via Shockwave I am seeing considerable lag and choppiness.

Video from the DVD player seems to need less processing and therefor is unaffected. By reducing the refresh rate I was hoping to relieve the main processor of some of the overhead of processing the video from Shockwave.

---

### Post by Yellow Pasque on 2010-01-31
> By reducing the refresh rate I was hoping to relieve the main processor of some of the overhead of processing the video
Reducing the refresh rate won't do that.

---

### Post by EmoDx on 2010-01-31
Other than a hardware refresh, can you think of any other ideas to get the shockwave to play better?  I tried Midori and it seemed to play a little better, but nothing to cheer about.

---

### Post by EmoDx on 2010-01-31
I tried looking for > /etc/X11/xorg.conf  and couldn't find it on my system. I enabled "show hidden files" option also. Any ideas?

---

