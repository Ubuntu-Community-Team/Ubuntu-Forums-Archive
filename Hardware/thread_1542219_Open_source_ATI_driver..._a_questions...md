---
title: "Open source ATI driver... a questions.."
date: 2010-07-30
forum: Hardware
---

### Post by request_another on 2010-07-30
When will the open source ATI driver have performance management (not too sure what its called). I had the open source driver installed and everything runs smooth, compiz effects are nice etc. But my laptop runs at about 10-15 degrees hotter than in windows when in performance mode.

I went and installed the proprietary driver and now my heat issues are gone. It runs the same temp as in windows 7. But now my problem is that i get a lot of stuttering with some compiz effects. Minimizing and maximizing are stuttery etc. This is quite annoying but i think i'll have to put up with it because i dont like having those heat issues.

So are there any plans to solve the heat problem with the open source drivers? Is there any way to solve the stuttering problem with the proprietary driver?

I have an hd mobility 3470 btw running on a Sony Vaio FW if thats important.

---

### Post by odyssey41 on 2010-07-30
I have exactly the same problem. Sony VAIO FW290 with ATI RadeonHD 3650. Laptop runs properly but very hot when using open source driver. Temperature problem goes away and computer runs basically as cool as when running Win 7 BUT video issues appear. Video playback using VLC or any other video player shows video stuttering significantly. Performance suffers a lot. This happens with 10.04 and also with 9.10. Obviously problem is not related to Ubuntu version but most likely with video driver used.

---

### Post by request_another on 2010-07-30
I solved the problem with some searching around :)

[http://ubuntuguide.net/how-to-fix-3d-performance-of-ati-driver-in-ubuntu-10-04](http://ubuntuguide.net/how-to-fix-3d-performance-of-ati-driver-in-ubuntu-10-04)

Everything's nice and smooth, and i have a nice cool system! So happy!

edit: ok everything's not ok, some games graphics are glitching.

---

### Post by sydbat on 2010-07-30
> **wankingweiner said:**
> I solved the problem with some searching around :)

[http://ubuntuguide.net/how-to-fix-3d-performance-of-ati-driver-in-ubuntu-10-04](http://ubuntuguide.net/how-to-fix-3d-performance-of-ati-driver-in-ubuntu-10-04)

Everything's nice and smooth, and i have a nice cool system! So happy!

edit: ok everything's not ok, some games graphics are glitching.Turn off 'Visual Effects' and see if that helps. System > Preferences > Appearance > Visual Effects tab.

---

### Post by request_another on 2010-07-30
the stuttering has been solved.

But now one of my games (the one i play the most), the tetris clone game has graphics problems. Funnily enough turning off visual effects fixes the game, but i want visual effects on.

---

### Post by request_another on 2010-07-30
Wow its been an eventful day.

I think i solved everything now. All i did was install the latest ATI driver from their site. Now there's no stuttering, the game works fine, and on top of that my laptop's brightness controls work too (they didnt before).

---

