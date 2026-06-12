---
title: "Webcam and DTV tuner card"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by dvillaveces on 2007-08-29
A week ago, my windows installation died, and I started having all sorts of trouble re-installing, so I decided to give Linux a try, Boy, am I impressed!! Ubuntu linux is one of the easiest and more  stable operating systems I have ever dealt with!!

There are 2 problems remaining, however:

1. I had purchased a Microsoft Lifecam to use with Skype, so Mum & dad (who live in the other side of the world) can see their grandchildren. Although the "Hardware Information" application does display the webcam under the USB Hub, I can not seem to make it work. I tried Skype and Camorama, and neither recognises it. 

2. I also recently purchased a 'MobiDTV Pro" USB Digital TV Tuner, and it worked great on my windows install. Again, I can see it in the "Hardware Information" application, but can't get it to work on MythTV.

Does anyone have any idea what can I do to solve these 2 problems? Your assistance will be *really* appreciated; I do not want to go back to Windows, but these 2 pieces of hardware are quite critical for me.

Thanks,

Diego

---

### Post by geoffatmk on 2007-12-15
I see there have been no responses to this request.  I also have a V-Gear MobiDTV usb stick and woulod like to use it with Myth TV on my ubuntu machine.  Can anyone o ffer any help on this please? 

Actually, even under windows I had problems getting it recognised but I am sure the linux community can help us solve this problem?

Geoff

---

### Post by oneiota on 2007-12-28
You've probably sorted this out by now, but I have a logitech webcam that failed to work when I plugged it into a USB hub (even though it was listed when I did a 'lsusb'), and the moment I plugged it into a dedicated USB socket (not a hub socket) it worked brilliantly.

---

### Post by geoffatmk on 2007-12-31
Thanks for your input one!ota.  However it does not help either of us with our digital TV stick problem.  I always insert this direct to the machine, not via a hub and it makes no difference.  Is there no one in the Linux community that has cracked this one?

Happy New Year to one and all for 2008

.:popcorn:

---

### Post by oneiota on 2008-01-02
Hi there, sorry the problem still exists.  I was commenting on the first item (in first post) and btw Skype has a beta release now with support for video in linux (I just got this working with my USB webcam).

As for the tuner issue, I have an internal tv tuner card (rather than USB) and that took a bit of tinkering before it would work, and it only works with Kaffeine for me.  Unfortunately, I don't know which package managed to do the job in the end.

I hope you can some advice on the latter.

---

### Post by tedrogers on 2008-03-30
Hmmm...same problem...I just bought one out to try with Mythbuntu (the Ubuntu / Myth distro) and I'd like to know how to get it to work too.

I thought it would just pick it up or something, but I get nothing when plugging in to the USB.

However, when if I then do a "lsusb" I get this output:

```
Bus 004 Device 009: ID 14aa:022a AVerMedia (again) or C&E 
```

I've checked and double checked, and this certainly seems to relate to the MobiDTV USB dongle.

I ultimately want to build a Media PC in my front room around Mythbuntu, and I've fallen on the first step.   :(

Is there like an equivalent of ndiswrapper but for windows drivers for MobiDTV?

Any ideas anyone???

---

### Post by tedrogers on 2008-04-05
Bump. Bump.

The weird thing is that somehow I managed to get the MobiDTV recognised in Myth the other day, and now I can't repeat it. Now all I get is an error as Myth fails to probe it as a capture card.

This is weird.

Anyone?

---

### Post by Mrs_JWM on 2008-04-21
Although we're running Windows Vista, I wonder if we may have had a similar problem with our HP Pavilion Elite m9040n TV Desktop and our Logitech Quickcam Chat.  Every time we tried to webcam in Yahoo or AIM, the window was black.  The video as viewed through the webcam software was fine, though.  It turned out our TV tuner card was the default video source.  Now we disable that before we webcam, restart, and we're good to go.  We can enable it again without restarting when we want to watch TV again.  This may not be your problem, but it's worth a shot!

---

