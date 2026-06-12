---
title: "time to trash an ATI 9600pro?"
date: 2009-11-26
forum: Hardware
---

### Post by 3zrael on 2009-11-26
Hello everybody,
a couple of days ago, I installed Ubuntu 9.10, everything was fine, but I noticed that web browsing is now really slow: I think is something related to my video card's drivers.

I have an old Ati Radeon 9600 pro, that was working quite well with Ubuntu 8.10. Now, what do to?
I would want to buy a faster video card, pheraps an Nvidia one, knowing that GeForce card have good Linux support (is that true?).

What would you suggest? is there a way to improve driver support for my old 9600pro or the time has come to choose a newer model? (considering my AGP slot...) At the moment, I did not installed any driver, I'm just using the default one.
Which model would you buy considering that I only need a decent web browsing experience? 

Thank you!
(...and sorry for my poor english...)

---

### Post by joe_pacific on 2009-11-26
Hi, 

My first instinct is that there is no video card problem, and that web browsing is slow due to something else. Do any other internet programs (bittorrent, email) also seem to be running slowly? There is probably a network problem that is causing your internet to run so slow.

If your radeon 9600 was having a problem, it should affect ALL windows, not just your web browser. Do other programs seem to work ok?

I would maybe test your internet connection by going to a site like [www.speedtest.net](www.speedtest.net). 

Let me know about other programs, and don't spend money on a new card just yet (I think the radeon 9600 is relatively well-supported on linux)!

Cheers

---

### Post by 3zrael on 2009-11-26
Thank you for your answer :)
Well, my internet connection speed is ok, all that I can report to you is that the desktop too isn't running so fast (I disabled all desktop effects, when with the 9.04 I kept them turned on)...
But when I watch a video on youtube (as an example) I cannot even scroll the page with the mouse wheel, everything is quite freezed, and the cpu is running at 100%...

---

### Post by 3zrael on 2009-11-26
do you think that my computer (athlon 3200xp) is just too slow to run properly Ubuntu 9.10? :(

---

### Post by cascade9 on 2009-11-26
Your XP 3200+ should be more than fine with 9.10. 

I would guess that you have driver issues, and/or flash issues. From what I know, the 9600 was discontinued from FLGRX in 9.10. If you havent already, try to manually install the 9600 driver from the ATI site- 

[http://www.amd.com](http://www.amd.com)

If that doesnt help, I'd look at your flash drivers. 

BTW, nVidia probably has better support with linux, but finding an AGP card to replace the 9600 would not be a fun job. Its hard to find AGP cards now, and the once that are around are not much better than the 9600 you have.

---

### Post by 3zrael on 2009-11-26
I already downloaded the catalyst drivers from ati's web site, but the installation doesn't start... :(
I agree with you, it must be something like a driver issue, and if I won't be able to solve it, probably I'll buy an old nvidia agp card... the other option would be to change motherboard, cpu and ram...

---

### Post by joe_pacific on 2009-11-26
> **cascade9 said:**
> Your XP 3200+ should be more than fine with 9.10. 

I would guess that you have driver issues, and/or flash issues. From what I know, the 9600 was discontinued from FLGRX in 9.10. If you havent already, try to manually install the 9600 driver from the ATI site- 

[http://www.amd.com](http://www.amd.com)


Do you think that switching to the ATI open source driver would fix the problem?

---

