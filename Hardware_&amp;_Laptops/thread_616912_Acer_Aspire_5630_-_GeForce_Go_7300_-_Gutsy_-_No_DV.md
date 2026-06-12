---
title: "Acer Aspire 5630 - GeForce Go 7300 - Gutsy - No DVD Playback"
date: 2007-11-18
forum: Hardware &amp; Laptops
---

### Post by Giggity on 2007-11-18
I've used Ubuntu on my desktop since Dapper last year, and have used it on my Acer Aspire 5630 laptop since Feisty.  The laptop has a problem reading encrypted DVD's (unencrypted ones work fine), and I'm out of creative solutions.[LIST]
[*] I've tried [this advice]("https://help.ubuntu.com/7.10/musicvideophotos/C/video.html#video-dvd") at the Official Docs site
[*]I've read through [this thread]("http://ubuntuforums.org/showthread.php?t=586928"), where I found out how to install libdvdplay0 (it wasn't in the repositories).  VLC won't play... it just closes after thinking for a minute.
[*]I heard that the DVD drive included with the 5630 (Matsushita UJ-850S) does not come with a hardware-encoded region, so I installed [regionset]("http://packages.ubuntu.com/gutsy/utils/regionset") and set the drive to Region 1.  That didn't solve the problem.
[*]I've even tried installing Linux Mint 4.0 "Daryna" since I heard that Mint comes with all the multimedia playback goodies preinstalled.  Same issue occurs.
[*]I have installed libdvdcss2.
[*]I have installed libxine1-ffmpeg.
[*]I have tried using gxine, totem, vlc and kaffeine.[/LIST]I couldn't do anything at all until installing libxine1-ffmpeg.  Now at least the DVD will start, but once I hit "Play Movie" in the DVD menu, an error message pops up:  "Message from the xine engine:  Encrypted media stream detected,  Media stream scrambled/encrypted"

Does anyone have any more ideas?  This seems to be the only problem I have in Gutsy, so if I can fix it, I'll be thrilled.

Thanks!

---

### Post by GoonerLander on 2008-01-02
I can second this, with almost identical symptoms, although I'm on an Asus C90S. Same DVD drive, though: Matshita UJ 850S. I'm in Ubuntu 7.10. Put a DVD in, it appears on the desktop, but it won't play in any player -- the player dithers momentarily and then aborts (in VLC, it just folds back to the "doing nothing" appearance, with no video screen and no activity; Gxine gives a read error; all other video players give similar errors).

---

