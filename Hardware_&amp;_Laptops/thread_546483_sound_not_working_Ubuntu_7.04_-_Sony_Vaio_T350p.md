---
title: "sound not working Ubuntu 7.04 - Sony Vaio T350p"
date: 2007-09-08
forum: Hardware &amp; Laptops
---

### Post by turtledude558 on 2007-09-08
Hi, I know that this has been posted so many times before, but what I was able to try hasn't worked, or is for an older distribution or I just wasn't able to understand it very well.

I'm having trouble with the sound on my Sony Vaio T350p. When I plug in headphones, I can hear the sound very faintly if the volume is turned up to the max. 

This is what I found out my sound card to be...
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

I would really appreciate anyones help because this is the 2nd time this has happened to me. I had Linux installed before, couldn't get the sound to work so uninstalled it. I really want to get away from Windows and I don't like macs, so I would really like to keep the Ubuntu Linux distribution as I'm getting a bit used to it.

Any help would be greatly appreciated, thanks.

---

### Post by lenticular on 2007-09-18
Ah, this sounds so familiar from adventures I had with my Vaio T340P.  This is from memory, but see if this helps:

1) from terminal, run alsamixer
2) if I recall correctly, you will columns with slider switches for all of you input and output devices
3) scroll rightwards, and find the slider that is either "external amp" or "preamp"
4) set that to be off and see if you have sound.

Good luck!

-John

---

