---
title: "Edgy Eft and High Definition Projection TV"
date: 2006-12-08
forum: Hardware &amp; Laptops
---

### Post by jon3k on 2006-12-08
I'm trying to connect a PC running Ubuntu 6.10 to a Hitachi 57F510 rear projection high-def television using a ASUS 6200AGP via the DVI port using a DVI to HDMI cable.  During dpkg-reconfigure xserver-xorg it even detected the television as "HITACHI PTV", which is definitely a good sign :)

I installed the lastest nvidia drivers off the NVIDIA website, and selected every resolution.  After restarting X, it ended up negotiating a resolution of 1280x720 (and the TV telling me it was operating at 720p).  

The problems are:
1. I'd like at least the the option of choosing 1080i, but I assume the card doesn't support interlaced output via the DVI port or possibly at all?  Not sure, hoping someone can enlighten me.
2. The output from the video card at *all* the resolutions I tried hangs off the edges of the television display.  I can't see the bars at either the top or the bottom of the screen after logging into X Windows.

Any input would be greatly appreciated!

---

### Post by Jason_25 on 2006-12-08
This is a pretty serious problem with the nvidia drivers right now. I've had 1080i working with various problems on a couple different driver versions.  The problem is that Nvidia keeps changing things around with the driver that breaks my previous "workarounds" in the xorg.conf.  Nvidia themselves seem confused on how to deal properly with the edid data from large digital displays, especially interlaced ones.  There are some workarounds on nvnews but you may have varied success.  For the time being, I just leave my HD direct-view CRT on 720p.  My friend with a 1080i rear projection is not so lucky.  His TV doesn't take 720p so for now he is stuck with 480p.

Problem #2 is normal.  When you watch movie content it will look fine.  If you don't like the looks of having your DE cut off, you could for instance start mplayer or whatever game you want to play in it's own xserver.  For gaming on 720p with overscan, I just set my games to window mode and size them to fit in the non-overscanned area.

---

### Post by jon3k on 2006-12-08
Youch. ](*,) 

I've done a bunch of reading on avsforum and on nvnews today (probably too much), and looks like I'm kind of out of luck on the "overscan" issue.  

If all I wanted to do was watch video via myth and play games I'd be fine, but I also just wanted to have a full blown linux PC in the living room, so I could browse the web, check e-mail, etc.  

Thanks for the response, I appreciate it.

---

### Post by rabidsnail on 2007-02-24
You might be able to work around problem #2 with xrandr.

---

### Post by Jose Catre-Vandis on 2007-02-24
I found the only way I could stop overscan was to run the same resolution on my monitor as on the TV (I needed to do this with monitor attached or not, but slightly different as i was using SVideo tv-out).

---

