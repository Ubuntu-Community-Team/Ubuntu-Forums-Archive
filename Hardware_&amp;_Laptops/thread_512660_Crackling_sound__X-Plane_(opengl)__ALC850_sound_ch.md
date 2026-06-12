---
title: "Crackling sound / X-Plane (opengl) / ALC850 sound chip"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by MikkelGH on 2007-07-29
Hi,

I have a problem which I'm unable to troubleshoot myself (and by using google). When I play X-Plane the sound is braking up and gets distorted by some kind of white noise (crackling sound).

My sound-card is an onboard realtek alc850 (on an MSI K8N NEO4-K motherboard). Strangely, if I plug-in my rather old (1st generation) SBLive card the noise *almost* disappears but however not entirely.

I have tried using the drivers delivered with the latest kernel (2.6.22.1) and also the realtek drivers. Nothing seems to cure the problem. THen I read that the microphone could interfere - disabling it didn't help either.

At the moment I'm a bit lost. One could argue why not just use the old SBLive card (given that its components are probably better anyway)... well, it doesn't support EAX2 and what not of all the fancy new stuff that has come out since year 2000, the realtek one does.


Hope any of you can provide some fast and useful response - judging by the many unanswered posts on the internet on the same issue leaves me a bit disillusioned, though.

EDIT: The sound works without problems in ally other applications and in Windows XP as well. It leads me to think perhaps X-Plane has a problem with the realtek chip?


Kind regards,

Mikkel G. Hangaard

---

### Post by sblanzio on 2007-11-03
same problem here with a ATI-Azalia HDA on-board soundcard. (from Asus A2M-MVP mainboard).

Sound is very crackling with X-plane, and even with TeamSpeak.

I think this is related to OSS sound manager which is used by both these applications. I keep hearing "CLICKs" during all the session (sometimes less after some time) and even engine sound is randomly muted for short instants.

If anybody can give us a hint this would be really appreciated.
thanks!
sblanzio

EDIT: I already tried with aoss

---

### Post by Icarosaurus on 2008-06-02
I have the same problem with a Nvidia Soundstorm on an Abit AN7 Motherboard.
I use OSS, cause the old proprietary drivers are OSS.

---

### Post by sblanzio on 2008-06-12
i finally solved my problems using the info i found in this post:

[http://ubuntuforums.org/showpost.php?p=4869171&postcount=16](http://ubuntuforums.org/showpost.php?p=4869171&postcount=16)

then i can start both teamspeak and xplane with aoss and works great!!

hope this can help

---

