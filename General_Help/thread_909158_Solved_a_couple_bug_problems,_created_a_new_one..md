---
title: "Solved a couple bug problems, created a new one."
date: 2008-09-03
forum: General Help
---

### Post by detroit/zero on 2008-09-03
For the last couple months, I've been having a heck of a time with ridiculously slow USB file transfer speeds, as outlined in posts [here]("http://ubuntuforums.org/showthread.php?t=895386") and [here]("http://ubuntuforums.org/showthread.php?t=793688").

Somewhere, out of the blue, and for no good reason I could find, I got [stuck in an endless login-loop]("http://ubuntuforums.org/showthread.php?t=906742") and had to resort to using failsafe gnome mode to use my computer. What a pain.

A couple forum posts and a complete lack of help from anyone, I found the perfect solution to both the problems:

I re-installed from scratch.

Initially disgruntled with regular gnome and regular Ubuntu in general, I decided to try the KDE flavor. I've always shied away from other OSs because they come with KDE as the default WM - I don't know why, and I can't really qualify it, but I just don't like KDE. Sue me.

My foray into the unknown with Kubuntu 8.04 and KDE 4 only reaffirmed my distaste for all things K. (Why *does* everything that installs in KDE have to start with a K?) Less than twelve hours later I wiped Kubuntu and re-installed regular Ubuntu.

Then it dawned on me: The horrendously slow USB file transfers have been tracked down to GVFS. Unable to [downgrade]("http://ubuntuforums.org/showpost.php?p=5705352&postcount=10") to a previous, fast-working version that didn't spend 45 minutes moving a 1GB movie file to an external USB hard disk, I would just neglect to update it when my install was complete and the inevitable system update message appears on first boot.

Unsure whether the actual problem lies in GVFS or in Nautilus, or whether an upgraded Nautilus relies on an upgraded GVFS, I waded through 289 updates and unchecked those particular ones.

Sure enough, check the attached screenshot. Over 20Mb/s transfer speed - read speeds of closer to 30 - when 10 was the absolute best before, and it always downsloped to 2.5 or 3Mb/s.

Now, the problem: GVFS and Nautilus are still un-upgraded, and my system update icon is stuck in the panel. I'd hate for a bunch of real updates to come through one day and forget to tick those back off and end up where I started.

How can I make it so that Nautilus and GVFS don't update? How can I freeze those two packages so they don't appear in the update list?

---

### Post by Peter09 on 2008-09-03
Find the package in Synaptic. Select it and then go to the Package Menu at the top of the window. There you will find an option to lock the version.

PC

---

### Post by detroit/zero on 2008-09-03
Perfect. Gracias, amigo!

I never knew that was there.

---

### Post by Zorael on 2008-09-03
> **detroit/zero said:**
> My foray into the unknown with Kubuntu 8.04 and KDE 4 only reaffirmed my distaste for all things K. (Why *does* everything that installs in KDE have to start with a K?) Less than twelve hours later I wiped Kubuntu and re-installed regular Ubuntu.
And you're saying Gnome programs don't start with G:s? ;)

gimp, gparted, gaim, gftp, ghemical, ghex, ghextris, ghfaxviewer, gnomoradio, gnotime, gimageview, gsoko, gcompris, gtetrinet, gthumb, gtodo, gtorrent-viewer, gtranscode, gtranslator, gtweakui, gtwitter, gtypist, gucharmap, gpicview, gfax, gfaxviewer, gqview, gquilt, gqcam, gwenview, gwhois, gworkspace, gwenrename, gweled gzilla, gzip, etc.

(Some of those may not be gnomey.)

It's like WinZip, WinRAR, WinDVD, WinCustomize, WinAce, WinProxy, WinOptimizer, WinMail, WinPatrol, WinAVI, WinDirStat, WinMorph, WinImage, WinASO, WinSCP, WinDVR, Winamp, WinTV, WinBoost, etc.


I think it's cute. Well, the Win* prefix has been done to death.

---

### Post by detroit/zero on 2008-09-03
> **Zorael said:**
> gimp, gparted, gaim, gftp, ghemical, ghex, ghextris, ghfaxviewer, gnomoradio, gnotime, gimageview, gsoko, gcompris, gtetrinet, gthumb, gtodo, gtorrent-viewer, gtranscode, gtranslator, gtweakui, gtwitter, gtypist, gucharmap, gpicview, gfax, gfaxviewer, gqview, gquilt, gqcam, gwenview, gwhois, gworkspace, gwenrename, gweled gzilla, gzip, etc.

Ya got me there. ;)

---

### Post by detroit/zero on 2008-09-07
Possible explanation for slow transfers and definite fix here:_ [http://ubuntuforums.org/showthread.php?t=911052](http://ubuntuforums.org/showthread.php?t=911052)_

---

### Post by detroit/zero on 2008-10-19
Since the slow USB write problems aren't limited to Ubuntu, and seem to apply to various distros and kernel versions over the last few years, I started [a thread over at Linuxquestions.org]("http://www.linuxquestions.org/questions/linux-hardware-18/slow-usb-write-speeds.-677588/")
 
 Maybe the people who are having this problem can all get together and find a fix, rather than wait to see what trickles down from on high.
 
 Come over there and chime in with your experiences with the slow USB write speeds.

---

