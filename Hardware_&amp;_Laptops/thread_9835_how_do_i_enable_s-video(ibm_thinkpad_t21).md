---
title: "how do i enable s-video(ibm thinkpad t21)?"
date: 2005-01-01
forum: Hardware &amp; Laptops
---

### Post by rudeboyskunk on 2005-01-01
i guess i should first mention that on my laptop i'm running fedora c3, not ubuntu(ubuntu is on my desktop...which is funny, everything would probably work better if i had ubuntu on the laptop and fedora on the desktop considering the other 3 million problems i have)...

but anyway, i have the svideo cable connected to the svideo connection on my computer and the svideo in connection on my tv, but it's not showing up on the tv...so how do i enable it in fedora c3???

---

### Post by Soulman on 2005-01-03
Well I'd first try connecting the s-video cord to the laptop and restart the laptop to see if the video card picks up the tv at that point.  Then if it is a card that acts similarly to my radeon then you may have to use the vesa drivers in order for the card to use the video for your desktop on the tv.  So just try restarting the laptop with the cable plugged in and see what happens.  That's my first suggestion.

---

### Post by Soulman on 2005-01-03
You may also want to try reducing the resolution of your laptop before trying to switch it to s-video.  Some tvs can't go above 800x600.

---

### Post by Soulman on 2005-01-03
[http://www.probo.com/timr/s3s.tgz](http://www.probo.com/timr/s3s.tgz)

This is a utility for using the s-video driver supplied for your s3 savage card.

[http://mr.uue.org/gnulinux/t20/](http://mr.uue.org/gnulinux/t20/)

I found this website may be of some use also.  So you should be able to continue using the savage drivers and use the utility in making use of your s-video card.  Hopefully this last post will do the most help.  See you online!

---

### Post by rudeboyskunk on 2005-01-05
thanks yall, i appreciate the tips!  i'm gonna try em all right now...

---

### Post by ethos101 on 2006-12-02
So how do I use that utility?  I have a T23 and need to use the s-video output.  Where do I extract the s3switch files?
:edit:
Nevermind got it, now I need to apply [this](http://ck.org.ua/dev/s3switch.patch) patch.  How do I go about doing that?

---

### Post by odzx on 2006-12-16
bump

---

### Post by PatrickMay16 on 2006-12-18
Bump.

---

