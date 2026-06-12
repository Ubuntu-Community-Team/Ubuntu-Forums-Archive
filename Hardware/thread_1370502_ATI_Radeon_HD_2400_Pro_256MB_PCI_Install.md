---
title: "ATI Radeon HD 2400 Pro 256MB PCI Install"
date: 2010-01-02
forum: Hardware
---

### Post by JSeymour on 2010-01-02
Hi All,

After my [attempt to install an nVidia GeForce 6200 256MB PCI in my new-to-me Dell PowerEdge 1600SC failed]("http://ubuntuforums.org/showthread.php?p=8588022#post8588022"), I did Yet More Research and, following reports the ATI Radeon HD 2400 Pro works on my machine, ordered one.  Now come the questions.  **Assuming** this card actually does work in my machine:
[LIST]
[*]Which driver do I want: The proprietary one or the open source one?
[*]In either case: Are the latest & greatest drivers available from the "regular" repos, do I need to add a new/special/experimental/whatever repo to get the latest driver?  Do I need to manually download and install from somewhere?
[*]Any hints about a procedure to follow if Things Go Wrong?
[*]Any hints on optimizing acceleration and 3D performance
[*]Any hints about dual-monitor (aka: double-headed) operation?
[*]I think I actually saw somebody have a problem with no sound after installing one of these.  I think the suspicion was that the ATI card was "stealing" the audio from his sound card.  How to prevent this?  (I have a CL sound card that's working quite well, thankyouverymuch.)
[/LIST]

I've searched and searched, and found all of the  above to be issues, or have been issues, at one-time-or-another.  Would like to get the latest skinny on it all, if possible.

Thanks,
Jim

---

### Post by JSeymour on 2010-01-03
*chirp* *chirp* *chirp*...

Hello?  Anybody here?

:)

---

### Post by JSeymour on 2010-01-06
Answering my own questions, from stuph found elsewhere on the 'net...

> **JSeymour said:**
> Hi All,

Which driver do I want: The proprietary one or the open source one?
Since the open-source driver requires kernel 2.6.32 if you want 3D graphics acceleration *with my card*, it was either upgrade my kernel to an unsupported config or go with the proprietary driver.  I chose the proprietary driver as the path of least resistance.  It seems to be working well

> **JSeymour said:**
> In either case: Are the latest & greatest drivers available from the "regular" repos, do I need to add a new/special/experimental/whatever repo to get the latest driver?
The latest drivers are **not** to be found on the normal repos.  You need xorg-edgers repos for the open-source drivers.  You need to manually download and jump thru hoops for the latest proprietary drivers.  N.B.: I found what was in the "restricted" repo to be working fine, so far.

> **JSeymour said:**
> Do I need to manually download and install from somewhere?
See above.

> **JSeymour said:**
> Any hints about a procedure to follow if Things Go Wrong?
Do a **lot** of reading :D

> **JSeymour said:**
> Any hints on optimizing acceleration and 3D performance
Same.

> **JSeymour said:**
> Any hints about dual-monitor (aka: double-headed) operation?
Same.  (Not going to repeat it all here.)

> **JSeymour said:**
> I think I actually saw somebody have a problem with no sound after installing one of these.  I think the suspicion was that the ATI card was "stealing" the audio from his sound card.  How to prevent this?
There are three ways: Blacklist the ati sound driver.  Alter the order of modules installs.  (Those two will have system-wide effects.)  Choose the source with the pulseaudio volume control.

I got the ATI Radeon HD 2400 Pro 256MB PCI card installed last night.  Works like a champ, so far, with the plain ol' ATI proprietary drivers.  I did *not* have a problem with the sound.  I think that only happens with the open-source radeon or radeonhd drivers.

Btw: With the ATI Rage XL I was getting around 50-100 fps max.  With the new card I'm getting more like 5000 fps :D

---

### Post by redrings on 2010-03-04
Just ordered one of these for a dell optiplex 755 after a failed attempt at installing a geforece 8400GS (needed 300watts, 755 only supplies 280).  

I'm hoping for dual screen with compiz in ubuntu.  Have you tried doing a dual screen setup with this card yet?

Thanks!

---

