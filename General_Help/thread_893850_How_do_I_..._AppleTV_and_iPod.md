---
title: "How do I ... AppleTV and iPod"
date: 2008-08-18
forum: General Help
---

### Post by clievers on 2008-08-18
Hey everyone,

So I've been thinking about getting an iPod Touch and an AppleTV but am unsure of how they can access my music/movies/images which are stored on my Ubuntu Feisty server. Is there a way to create an iTunes library in Ubuntu to "share" out, or is there another way of going about this? From what I understand, this is the method by which iPod Touch and AppleTV go about seeing multimedia.

Thanks.

---

### Post by clievers on 2008-08-25
So no one has run into this .. storing media on Linux and using an Apple product to play/stream it?

---

### Post by randipoling on 2008-08-25
Possibly because everyone that has an Apple TV has a MAC computer.  I suggest actually calling Apple to see what they say.

---

### Post by sricketts on 2008-08-25
I have been toying with the same idea, but considered AppleTV only as an alternative. Another option is the squeezebox from Logitech, although I think it can only handle audio. You can serve the music using slimserver on your linux machine.

Anyway, I haven't done too much research on the topic but am interested in setting up something similar myself. I will update this thread if I make any progress.

-SR-

---

### Post by gnomeza on 2008-09-02
I have a media centre with an AppleTV frontend and debian box on the backend. I do not have an Intel Mac.

Without iTunes >= 7.6 you can't sync the AppleTV.

However, you can install plugins like Sapphire, ATVFiles, nitoTV, etc on the AppleTV, then mount your media server via NFS or Samba.

This allows you to play the vast majority of video formats playable through either Quicktime+Perian or mplayer, as long as you have the processing power. This makes the AppleTV a very effective little movie player.

Playing music via ATVFiles works, but the UI is terribly cludgy compared to the built-in AppleTV music player. There doesn't seem to be any better way to play music through the AppleTV

I'm currently trying to find a way to sync music to the AppleTV.
[LIST]
[*] Installing iTunes on the AppleTV itself:
  iTunes 7.5 works beautifully, but doesn't support AppleTV syncing.
  iTunes 7.6 requires OS X 10.4.9, ATV currently uses 10.4.7

[*] iTunes 7.6 under wine
  Supposed to work, but installation fails for me (wine 1.1.0, Debian Etch x86_64)
  No reports of syncing with AppleTV working under wine
[/LIST]

---

### Post by cgunther on 2008-10-15
Anyone have any success with this yet?  I'm running Ubuntu with a RAID-1 array.  I put all my movies, music, podcasts, etc on this array.  Right now I just mount this as a Samba share and access it from my PC and point iTunes at that Samba drive.  I then share the iTunes library so I can watch all my movies and listen to my music on the AppleTV.

I would like to pull the PC/iTunes out of the mix and serve the movies/music directly from Ubuntu.  If this can be done, how do you complete the registration that AppleTV requires everytime you attach to a new share (this is the part where you have to go back to iTunes and key in the 5-digit code given to you by the AppleTV)?

---

### Post by gnomeza on 2008-10-20
> **cgunther said:**
> ...how do you complete the registration that AppleTV requires everytime you attach to a new share (this is the part where you have to go back to iTunes and key in the 5-digit code given to you by the AppleTV)?

The short answer is - you can't. No-one has reverse engineered Apple's authentication method.

An alternative is now using [XBMC for AppleTV]("http://xbmc.org/wiki/?title=XBMC_for_Mac_on_Apple_TV").

---

### Post by clievers on 2008-10-20
Yes, I came across that XBMC for AppleTV recently as well. Currently I believe it's still in Beta. Also, not sure if it would work on new AppleTV's (with newer software/firmware). But definitely one to keep an eye on.

I've recently purchased a PS3. I am playing around with Media Sharing on it right now. On my one linux box, I've installed MediaTomb, a UPnP media server. I set it to scan my video directory. It does work. Tonight / This week, I am going to install MediaTomb on my file server, music pictures and movies, and see how it is. My main problem right now, I think, is that the PS3 is much higher resolution then my xbox (currently using XBMC on old xbox), so any video's that aren't of the highest quality really show the defects on the PS3. But, more playing around to do...

---

