---
title: "Need Help Setting Environment Variables (gimp-gap problems)"
date: 2008-09-26
forum: General Help
---

### Post by aura eyes on 2008-09-26
Greetings,

I tried posting this in the 64 section (I have the 64 bit version), but didn't get a single reply.  Please help!

I'm having a bit of a problem with GAP in gimp. When I try to extract a video through XTNS/split video into frames/Mplayer based extraction, I get a message saying that mplayer 1.0 must be installed somewhere in my PATH and that if mplayer isn't in my PATH or isn't named mplayr, I have to set environment variable GAP_MPLAYER_PROG to my mplayer program and restart gimp.

I have mplayer.  The version is newer than 1.0, though (dev-SVN-r27536-4.2.3).  

I have searched for awhile, and I tried the command:

export GAP_MPLAYER_PROG=mplayer

Which did nothing

I did a:

which mplayer

which gave me this:
/usr/local/bin/mplayer

I think I might be able to add something to my ~/.profile or ~/.bashrc, but I'm not sure what to put in there.

I want to make a gif from a video file (like an avi). If there's a better program for this, then that would work too. Just seems that gimp (gap) could do it if I could get it do work.

I'm stuck. Please help. Thanks.

---

### Post by aura eyes on 2008-09-27
Please help. 

Any program that can do what gimp-gap does (especially making a gif out of a video) would also work.  Thank you.

---

