---
title: "Gentoo 2007 is out"
date: 2007-05-07
forum: Gentoo and derivatives
---

### Post by ahaslam on 2007-05-07
As the title suggests:
[http://www.gentoo.org/proj/en/releng/release/2007.0/2007.0-press-release.txt](http://www.gentoo.org/proj/en/releng/release/2007.0/2007.0-press-release.txt)

Fast downloads as well ;)

---

### Post by justin whitaker on 2007-05-07
> **Anthony Haslam said:**
> As the title suggests:
[http://www.gentoo.org/proj/en/releng/release/2007.0/2007.0-press-release.txt](http://www.gentoo.org/proj/en/releng/release/2007.0/2007.0-press-release.txt)

Fast downloads as well ;)

Wow. I might have to take another look. Hopefully, they fixed the installer. :)

---

### Post by Pobega on 2007-05-07
Finally, this means I can FINALLY install it on my laptop; The 2.6.16 kernel on 2006.1 didn't support my ethernet (Realtek) well enough for me to get a connection. Maybe now I'll be able to install Gentoo properly :D

---

### Post by FuturePilot on 2007-05-07
Hehe, perfect timing. I decided to download Gentoo and try it out. Then I realized they just released a new version:)

---

### Post by cotcot on 2007-05-09
> **justin whitaker said:**
> Wow. I might have to take another look. Hopefully, they fixed the installer. :)
I would still not use the installer.

---

### Post by zaratustra on 2007-05-09
I've managed to crash installer:) But there is an advance:))

---

### Post by Kingsley on 2007-05-13
I've always thought of Gentoo as a version-less distro.

---

### Post by igknighted on 2007-05-14
> **Kingsley said:**
> I've always thought of Gentoo as a version-less distro.

It is rolling release.  All a new release means is that there is a new installer available.

---

### Post by Ateo on 2007-05-14
> **Kingsley said:**
> I've always thought of Gentoo as a version-less distro.

That's because it is... well, actually, I think baselayout is what really defines gentoo's version... but that's just me.

--------

I downloaded the live CD. It crashed. So much for a GUI installer.

---

### Post by Compyx on 2007-05-14
I tried the LiveCD-installer, but for some reason the kernel-config dialog just asked me if I was finished without giving me a chance to actually configure my kernel. A lot of people have problems with the new installer, so I'd just use the netinstal-CD and do a ```
emerge --emptytree world
``` as soon as possible.

The netinstall method always works like a charm.

---

### Post by zaratustra on 2007-05-14
> **Ateo said:**
> That's because it is... well, actually, I think baselayout is what really defines gentoo's version... but that's just me.
 I agree with ya:) I hope baselayout-2.0.0 will became stable soon.

> **Compyx said:**
> I tried the LiveCD-installer, but for some reason the kernel-config dialog just asked me if I was finished without giving me a chance to actually configure my kernel. A lot of people have problems with the new installer, so I'd just use the netinstal-CD and do a ```
emerge --emptytree world
``` as soon as possible.

The netinstall method always works like a charm. This is probably because there is no kernel sources in livecd, is think, and it can installs only precompiled livecd kernel unless you use other method of install. I prefer to use cli install with stage3, and before compiling anyadditional packages, i usually do ```
emerge --oneshot system
``` on installed stage3 system, because all this installer stuff is freaky and I don't like to compile much stuff (glibc,gcc) on livecd environment, and effect is the same.

---

### Post by Ateo on 2007-05-14
The quality of the 2007.0 release leaves a lot to be desired. I've been a Gentoo user for 5 years and with each release, the quality just gets worse.

Don't get me wrong. I don't 'upgrade'. I just download the new ISOs to see what the new installer looks like. Looks like I will continue to use my trusted 1.2 Live CD. =)

---

### Post by justin whitaker on 2007-05-14
> **cotcot said:**
> I would still not use the installer.

Really? How bad is it? I really don't see the point of emerging out of a stage 3 install...it ties up my core system for too long, and I have yet to have a successful install that allowed me to get to KDE or Gnome after the endless compile. Complete waste of time to my mind, especially when Sabayon is out there providing a competing product that is easier to install and gets you to the same end result.

---

### Post by Ateo on 2007-05-14
> **justin whitaker said:**
> Really? How bad is it? I really don't see the point of emerging out of a stage 3 install...it ties up my core system for too long, and I have yet to have a successful install that allowed me to get to KDE or Gnome after the endless compile. Complete waste of time to my mind, especially when Sabayon is out there providing a competing product that is easier to install and gets you to the same end result.

++

Exactly. It's a waste of time, in my mind, to use the Gentoo live CD now that Sabayon Linux exists.

---

### Post by ThinkBuntu on 2007-05-14
I was so psyched for Sabayon...the DVD lagged for me, so I ordered a Mini CD (my burned copy didn't work) but I experienced Gentoo hell with OpenOffice. My first emerge (not ever, just on this system) was for openoffice. 5 hours later, it still wasn't finished. Next!

Granted, I'm on a laptop using open wireless networks. Maybe I'd see things differently on a higher-spec desktop with an ethernet hookup.

---

### Post by Ateo on 2007-05-14
You compile OpenOffice? You're brave.

---

### Post by Compyx on 2007-05-16
> **Ateo said:**
> You compile OpenOffice? You're brave.

I did that a few times, it only takes about 4.5GB disk space for intermediate files and many hours of cpu-time. Of course all that was before I found out about 'openoffice-bin'. ;)

---

### Post by Pobega on 2007-05-16
> **ThinkBuntu said:**
> I was so psyched for Sabayon...the DVD lagged for me, so I ordered a Mini CD (my burned copy didn't work) but I experienced Gentoo hell with OpenOffice. My first emerge (not ever, just on this system) was for openoffice. 5 hours later, it still wasn't finished. Next!

Granted, I'm on a laptop using open wireless networks. Maybe I'd see things differently on a higher-spec desktop with an ethernet hookup.

That's why they have OpenOffice.org binaries available. I believe Gentoo's binaries are limited to OOo, GNOME and KDE, but I could be wrong (Not a Gentoo user).

---

### Post by mips on 2007-05-16
> **Pobega said:**
> I believe Gentoo's binaries are limited to OOo, GNOME and KDE, but I could be wrong (Not a Gentoo user).

Wrong on the KDE & Gnome one. They have binaries for stuff like Java, Firefox, Seamonkey, diskreport, cromwell, ddcxinfo-knoppix, netlogo, wengophone, sancho, simpserver, staden, frostwire, nessus, mplayer, shoutcast, savage, stoned, hoh, drod and a whole bunch of games and other stuff etc.

---

### Post by Ateo on 2007-05-17
> **Compyx said:**
> I did that a few times, it only takes about 4.5GB disk space for intermediate files and many hours of cpu-time. Of course all that was before I found out about 'openoffice-bin'. ;)

I did that once. 6 hours later... uh hum.... just like I use to always do a stage 1.. 

After that and from then on saw use of the binary in portage.... hehe...

---

### Post by fakie_flip on 2007-05-21
I've got dual core now. I wonder how much that would speed up the the compiling. I can also overclock the cpu during the time I need to compile.

---

### Post by Enverex on 2007-05-21
Dual core (if you go on the premise that your previous processor was the same speed as a single core in your new dual core) is ~almost~ twice as fast, as long as the code that is being compiled allows for concurrent compilation. So that's nice (I assume it's virtually entirely CPU power dependant going by that).

---

