---
title: "xine based media players, xvid/mpeg4 out of sync"
date: 2005-12-01
forum: General Help
---

### Post by jdong on 2005-12-01
I just recently started using mencoder to convert my realvideo stuff over to xvid. The encoding process went very smoothly, but playback had some issues...

while using Xine based players (totem with xine backend, xine) there is a noticeable lag between the audio and video. This effect does not occur in the original realvideo file on both players, or with mplayer or VLC.

Is this a Xine issue? Anything I can do to pseudo-fix it?

---

### Post by scaine on 2005-12-07
I have the same issue with a brand new install of Breezy three days ago - Athlon 64 ISO.  Downloaded the gstreamer plugins from Multiverse/Universe.
Fraid I'm not too clever about telling the difference between Totem/Xine/Gstreamer/Mplayer versions I'm using - all a bit confusing under linux I find.  In my past 386 breezy installs I just downloaded Mplayer and used it, cos it was the only one that supported wma format (which I use at work out of necessity).

This time round, I'm using the Athlon 64 Breezy and out of the box, I'm experiencing the same 2 second lag between audio and video.  Also, fast forwarding/rewinding using Totem produces a "speed up" effect - you get a very smooth and fast video effect which puts the audio even further out of sync.

Can't be more help than to say "I have the same problem" though.

---

### Post by jdong on 2005-12-07
I've turned off esd / other sound servers in an effort to reduce the lag... Doesn't help much...

---

### Post by scaine on 2005-12-07
Not sure what happened here - I found recommendation to turn off esd (killall esd) and when I did, I found the lag fixed.

However, I have since reboot - esd is running again, but now I don't appear to have any lag.

Pretty confusing.  It's late though and I'm only giving the movies seconds to impress me with their lip-syncing, so I'll try again tomorrow and post back if there's still a problem...

---

### Post by jdong on 2005-12-07
lol; esd has been known to cause lag. It's the downfall of the audio server concept. This is not the first time I've experienced lag problems before; though my prior incidents were almost all sound server related.


since I encoded this video myself, and it sometimes plays fine and sometimes not, it seems like I can blame this on myself. However:

It seems like the audio stream should be encoded as cbr (constant bitrate) as opposed to abr or vbr.... The latter two seems to greatly worsen the lag.

---

### Post by scaine on 2005-12-08
[QUOTE=jdong]
It seems like the audio stream should be encoded as cbr (constant bitrate) as opposed to abr or vbr.... The latter two seems to greatly worsen the lag.[/QUOTE]

Interesting you saying that.  We use a cheap and cheerful Windows Media solution to stream TV over our network at work, using multicast.  I find that if we use VBR, then over time (usuallly a couple of days), we develop link syncing problems.  I use VBR (2Mb in this case) for the video stream (wma - it's a windows solution) and CBR 44K stereo for the audio.  Never get lipsync issues now.

As for my Ubuntu lipsyncing - damn.  It's defintely gone.  Movies are playing fine now.  I wish I knew what caused this, but killing esd is the only thing I can remember doing - and now everythings working, despite a reboot and esd being back on my process list.  Bizarre.

I'm looking forward to Gstreamer .10 though - there's a lot of hype surrounding that right now and the feature list really does look superb.  Fingers crossed this heralds the end of all Linux multimedia woes...  :)

---

### Post by jdong on 2005-12-08
I hope so too... can't wait till Dapper (no; I don't feel daring enough to backport the entire gstreamer stack to Breezy!)

---

### Post by scaine on 2005-12-08
Go on... you know you want to... :razz: 

On the other hand - I've seen your "accepted backports" list.  Sheesh.

Good luck!

---

