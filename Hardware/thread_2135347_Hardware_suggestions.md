---
title: "Hardware suggestions"
date: 2013-04-14
forum: Hardware
---

### Post by chrsbrss on 2013-04-14
Okay, here is the plan...

I currently have 3 Roku's in my home that I am streaming my movies to via an old AMD 2.2 GHz processor running Windows XP 64 bit OS.  I plan on building my own computer to replace it (due to it being slightly out of date) which I wan't to do the following.

1.  Stream videos to at minimum 1 Roku in HD with the potential to stream to at least 2 if possible.
2.  Capture live TV (via Mythbuntu) and store it as well as edit it to remove all advertisements and keep in storage for later viewing.
3.  Capable of being able to upgrade fairly easily further down the line when time and budget permit (upgrading RAM, HHD space and looking at possibility of putting OS on a SSD while keeping video storage in HHD - Is is possible to upgrade CPU without replacing Mother Board later?!?!)
4.  Light Internet usage - Does not need to occur if streaming, but would be nice - doing things like checking email and watching youtube due to the 'Plex it" capability's of Plex media server.
5.  Plug directly into the internet via Ethernet cable but up gradable to wi-fi at a later date (potential upgrade that I would be looking at doing later.

I realize that this sounds pretty simple, but I have never build a computer before, so I am slightly concerned about it, but do have a friend with considerable experience who will aid me.  I have absolutely no Linux experience, so hardware that is for the most part plug and play with little or no issues working with the compatibility of mythbuntu and ubuntu.  

I have budgeted $300 for the initial build but can throw in more if needed, the only thing I have in my possession is a tower capable of ATX with expansion of up to three HHD's and 2 Optical Drives, as well as a ASUS video card (model # unavailable at this time) and hope to accomplish at minimum 2.5GHz processor (Intel or AMD - Prefer Intel, but not opposed to AMD) with 4GB RAM and 1 TB HHD.  Hardware suggestions would be great to accomplish this build.

Thanks.

---

### Post by TheFu on 2013-04-14
If you just wanted to stream, I'd suggest a dual Atom box with a GigE network. Built a silent one of those last August for $170.

But, with the desire to record TV, remove commercials and transcode, then you need at least a Core i3 or Core i5 box to keep up.  4GB of RAM is fine.

Forget wifi for a server.  Streaming over wifi will never compare to wired eithernet. NEVER.  The Rokus can be connected via wifi, but not the server.  Wifi is not as stable as it seems when causally web surfing. Videos, especially HD videos, will stutter.  You might get lucky with 1 stream, but don't count on it. Wired for servers, that is the rule for very good reason.

You didn't mention a video recording card/tuner.  If in the USA, check out the network tuners from SiliconDust - HD-Homeruns.  I have one - love it.  Just needs to be somewhere on the network, not inside a specific box. This means lots of flexibility for your setup AND that another PC can also be a recorder if desired.

To remove commercials, check out comskip. You'll want an MPEG2 file for this, but mpeg2 storage is 60% too large, so transcoding to h.264 is highly recommended.  The issue that I have with removing commercials is finding a linux editing tool that supports .EDL or .CUT file formats from comskip. Comskip is not perfect, but very close 85% of the time. Manual correct is needed. Takes about 2 minutes per file using a Windows tool ... Video Redo Plus.

I'm interested in a linux editing tool that supports marked cuts from comskip. Hopefully someone smarter than us will post.

---

