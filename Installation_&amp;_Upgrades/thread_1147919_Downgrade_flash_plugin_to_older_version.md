---
title: "Downgrade flash plugin to older version?"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by zgembo on 2009-05-03
How can I downgrade flash plugin to older version? Currently 
I have the newest one but it doesn't work well, videos freeze for several seconds and then jumps. Watching youtube videos becomes very frustrating. With older version everything was fine.

---

### Post by lovinglinux on 2009-05-04
I'm in the same boat. Tried swfdec, gnash, downgraded my video driver. Nothing works. I didn't think about downgrading to flash 9. 

Did you upgraded or installed Jaunty recently? What version of Ubuntu are you using?

The recent Flash version (10.x) was working great for me on Hardy Heron. My problems started with Jaunty.

---

### Post by zgembo on 2009-05-04
For me it started with Intrepid. I see many people have same problem. Maybe because of video card?
Any idea where to download an older versions?

---

### Post by lovinglinux on 2009-05-04
> **zgembo said:**
> For me it started with Intrepid. I see many people have same problem. Maybe because of video card?
Any idea where to download an older versions?

I don't thin so. I did some tests and downloaded a flash video that was playing really bad on Firefox and opened it with VLC. It plays fine and uses much less CPU.

---

### Post by Marat Galiev on 2009-05-04
Remove package flashplayer.
Remove file /usr/lib/mozilla/plugins/libflashplayer.so (if exists).

Install older version.

---

### Post by zgembo on 2009-05-04
> **lovinglinux said:**
> I don't thin so. I did some tests and downloaded a flash video that was playing really bad on Firefox and opened it with VLC. It plays fine and uses much less CPU.

Nice idea !!!
How can I do that?

Edit: I found it here:
[http://www.pradimani.com/2009/03/23/problem-in-viewing-youtube-play-youtube-in-vlc-player/]("http://www.pradimani.com/2009/03/23/problem-in-viewing-youtube-play-youtube-in-vlc-player/")

Thanks for great idea .

---

### Post by zgembo on 2009-05-04
> **Marat Galiev said:**
> Remove package flashplayer.
Remove file /usr/lib/mozilla/plugins/libflashplayer.so (if exists).

Install older version.

How can I install older version?

---

### Post by zgembo on 2009-05-04
I don't know how but after I tried to play youtube videos on vlc, which worked perfect, suddenly everything else is also ok. Youtubr videos play directly smooth and nice. :confused:
I don't understand what happened but I like it.
:guitar:

---

### Post by fmmarzoa on 2010-02-09
As told before: How can WE install older version?

I did a search on Adobe's Flash site but didn't found exactly what I want: latests 9.x flash plugin for firefox and linux.

---

### Post by clicker4721 on 2010-02-09
> **zgembo said:**
> I don't know how but after I tried to play youtube videos on vlc, which worked perfect, suddenly everything else is also ok. Youtubr videos play directly smooth and nice. :confused:
I don't understand what happened but I like it.
:guitar:
To play them in VLC, did you download the videos or use the VLC plugin? And, how did you do whatever you did?

---

### Post by foresthill on 2010-02-09
I was having terrible problems with flash on my new install of 9.10 64 bit. Here is what I did to fix it:

[http://ubuntuforums.org/showthread.php?t=1401723](http://ubuntuforums.org/showthread.php?t=1401723)

No problems at all now.

---

