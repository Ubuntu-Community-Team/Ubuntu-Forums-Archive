---
title: "dvd lameness"
date: 2005-12-28
forum: Hardware &amp; Laptops
---

### Post by spiderworm on 2005-12-28
Hi all,

Running Breezy here and trying to get my DVD player working.  It's not happening.

I have the latest and greatest libdvdcss2 package.  When I try to play a dvd in xine, i get something like this in the terminal window:

libdvdread: Using libdvdcss version 1.2.9 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient
libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000011e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000018e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00004310
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0

Then xine pops up a "cannot read from source file or disk" error.

Totem spits out a similar string of messages in the terminal, then pops up this error:

"The source seems encrypted, and can't be read.  Are you trying to play an encrypted DVD without libdvdcss?"

Oddly enough, this is a box I mostly use for MythTV, and when I play a DVD in  MythTV, it tries to play and does much better than xine... very slow and choppy, weird artifacts all over the place, not anywhere close to where it would need to be in order to watch a movie, but at least better than xine.

Please, I dont know what info might be pertinant to get some help on this.  Please let me know what info you need and help me if you can.  Thank you.

spiderworm

---

### Post by spiderworm on 2005-12-29
Hey all,

I got dvd playback working, had to keep trying different versions of libdvdcss2 until I found one that worked, but now I can barely hear it!  Can anybody tell me what mixer channel needs to be bumped up to change the DVD volume independently of the other volumes (not Master, not PCM)?  I've been trying to find the right channels to mess with but with no luck so far...

The options I have in Kmix are:

Output:
- center
- LFE
- wave center
- wave lfe
- wave surround
- pc speaker
- ac97
- surround sound

Input
- surround
- synth
- wave
- Line
- line liveDrive
- line2 liveDrive
- CD
- Mic
- Video
- IEC958 LiveDrive
- IEC958 TTL
- Aux
- Capture

Thank you in advance for your help!

---

