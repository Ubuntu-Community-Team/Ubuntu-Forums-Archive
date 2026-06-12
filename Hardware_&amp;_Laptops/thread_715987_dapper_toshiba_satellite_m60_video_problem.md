---
title: "dapper toshiba satellite m60 video problem"
date: 2008-03-05
forum: Hardware &amp; Laptops
---

### Post by chelala on 2008-03-05
Hi

I have this toshiba satellite m60 video is intel 915

First the livecd did not work with the default video, so I had to use safe graphics. Then when installed I checked the xorg and driver says vesa, resolution is 1024x768 no video acceleration.

Following the ubuntu guide I downloaded some intel rpm, alien to it and then dpkg. Restarted and nothing

then sa alien showed a warning I used --scripts and dpkg but the told me could not compile because I had old modules or something. I have installed 2.6.15-51-386 and kernel headers too

Then I force it and edited xorg.conf and changed vesa for i810 and showed error like agpgart dir does not exists

Any help, any clue please?

Thanks, Chelala

---

