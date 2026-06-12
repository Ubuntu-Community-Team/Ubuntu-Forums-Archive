---
title: "Dvd::Rip error"
date: 2005-11-21
forum: General Help
---

### Post by vaskark on 2005-11-21
I received an error message when I tried to encode (after it got copied to my hd). It wouldn't let me copy/paste the message so I attached a pic. Can anyone figure out what's going on?

---

### Post by darknuala on 2005-11-22
The first thing I see is that it cannot detect your device name.  Make sure you go through the settings page, and make sure that at the bottom everything checks out as [COLOR="Red"]OK[/COLOR].  
Make sure you have all of the programs installed that Dvd::Rip requires.

---

### Post by jimmyj on 2005-11-22
I don't think that should be his problem since he already ripped to the hard drive. I get the same "error" when I rip to the hd and then transcode it with no problems.

The line that draws my attention is loading export_ffmpeg.so failed. Do you have ffmpeg installed properly? If so, what versions of transcode and ffmpeg are you using? I had problems on Fedora with the newest transcode and certain libararies. Downgrading alieviated those problems.

---

### Post by darknuala on 2005-11-23
That's what I was meaning about having all of the programs installed.  ffmpeg does indeed sound like the problem after re-reading the error.

---

