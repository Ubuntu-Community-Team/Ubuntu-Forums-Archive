---
title: "Xbox 360 HD-DVD Drive support?"
date: 2008-05-14
forum: Hardware
---

### Post by aristotlewilde on 2008-05-14
So today on a whim I picked up the Xbox 360 HD-DVD drive for $25.  

For the price, I couldn't pass it up, since at the very worst, it's an extra external DVD Drive AND an Xbox 360 remote for next no no money.

So I was wondering if anyone had developed the HD DVD codec/support for Linux yet?  

I plugged the drive in, and it was immediately recognized and played DVD's.  But when I popped in an HD-DVD, it was not recognized.

---

### Post by AstralPancakes on 2008-05-20
You could try the UDF2.50 kernel module from [this]("http://www.uluga.ubuntuforums.org/showthread.php?t=718744") thread. It compiles and inserts according to the instructions just fine for me, and HD-DVDs mount, but they're not shown as containing any files. Hmm...

I compiled a custom kernel for UDF2.50 in Gutsy, but I don't think I can be bothered doing that again.

Then after that you need something to decrypt the disc (not sure if there's anything that can do this reliably on-the-fly yet), and something to play it back (I hear a recent VLC and/or mplayer might do this).

---

