---
title: "diskless htpc"
date: 2008-10-04
forum: General Help
---

### Post by Bo Rosén on 2008-10-04
Hi all,
I'm looking for advice and tips on the best way to build a diskless htpc. My main PC will serve as the media server and old bits and pieces will be cobbled together into a diskless client. The client should work fine for my simple needs, I've used all the components before to watch video and so on. It's just meant to be a fun little project and not something I'm going to spend any money on at present, so please have that in mind if you comment.

As it is, I will mainly use it for watching video files, both stored and if possible, streamed from places like Miro.
If it turns out well, I might expand it at a later date by adding a tv-card, remote, hardrive and upgrade the old components.

I've been looking at mythbuntu, but it seems a bit much for my current needs but I don't know of anything else that supports this set up as well as mythbuntu does.

I imagine the hardest part will be setting up the network boot thingy (I don't have a router so the computers will be connected directly,  the sever will use eth2 and the client eth0)
There's a Windows XP box connected to the server on eth1 with a static ip to access the Internet, but no shared folders as I couldn't get that to work on Hardy. I only mention that because of the static IP thing.

Any general tips or pointers?

---

### Post by jvin248 on 2008-10-04
There's the liveCD Myth front-end option (would require adding the CDrom drive back).

The other option that might work is enabling LTSP - then it's like logging into your main server but from the remote thin client.  LTSP.org has the basics, though it's modified a little for Ubuntu.  Then the client can be diskless and only a P2-233Mhz or better machine with 128MB ram.

---

### Post by Bo Rosén on 2008-10-06
Thanks.
Tried Mythbuntu's diskless client but couldn't sort out the whole dhcp and booting over the lan thing to work. Besides, Mythbuntu is more than I want, Geexbox is closer if I can get it to find files on my server.

---

