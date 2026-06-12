---
title: "DVDs mounting as blanks and dvd ripping slowwww"
date: 2005-08-13
forum: Hardware &amp; Laptops
---

### Post by akutz on 2005-08-13
Specs:

Shuttle 83G5, Intel P4 2.8 HT, nvidia 6600, 1GB Crucial RAM, 2 160GB SATA WD HDs.  Most importantly, a Plextor 716a DVD-RW (etc, etc...)

I am using Hoary with the 2.6.10 SMP kernel.  I have also installed the nvidia drivers.

When I stick a DVD in the thing shows up as a blank disc.  DMESG shows that cdrom is unable to read the files on the disc.  I do have libcss2 installed, so I am severely confused.  

It gets weirder.  If I throw an audio cd in the drive first (reads fine), then eject it, and *then* put the dvd back in it will mount properly.

However, even after all this it still only rips at 2x.  I have DMA enabled.  I have autoplay turned off.  I have paranoia set to 0.  Help!  Ripping and shrinking dvds is something that I don't too infrequently so this needs to work or else Windows may have to stain my drive platters once more.

CDs will rip upwards of 9x most of the time, which takes about 6-7 minutes for a whole cd.  A DVD should *not* take 45 minutes to rip though.

This is the last thing to get to work for my shuttle config.  I am putting together a doc for the WIKI on my config for all those in need with the same hardware.  So you're not just helping me, you're helping the *children.*  : )

Thanks in advance for help!

---

### Post by akutz on 2005-08-13
Quick thought, my drive supports UDMA 4, should I throttle it down to 1, 2, or 3?

Also, if there is a DVD in my drive when the machine boots, gnome will show 2 mount points.  DVD-ROM Disc and DVD-ROM Disc (2).  The first one shows up as a blank disc (event though it is a movie) and the second one is not portrayed as a movie, but when I browse it I can see the AUDIO_TS and VIDEO_TS folders.

Suggestions?

Help!

---

### Post by akutz on 2005-08-14
Intteereeesssttinnngggg ...

I switced out my plextor for an old lite-on dvd burner.  Everything now mounts normally and I am getting dvd decrypt read speeds ~6x ... I am betting the current kernel just has issues with UDMA4 or the latest plextors ...

Good to know though ...

So it seems that some of these DMA issues that people are having *may* have to do with their brand of burner ....

---

### Post by akutz on 2005-08-14
It gets better ... the liteon can only seem to rip audio at ~5x, whereas I was getting 9x with the plextor ... so liteon is better for dvd ripping, but plextor is better for audio ... at least that is what my tests show so far ... I have the 451S liteon ... I am going to order the latest drive from newegg to see if it is any faster ... I have noticed that liteon needs to spin the media up first before it can really get a good speed going ...

---

