---
title: "Ubuntu 12.10 running slow on Aspire One 751"
date: 2012-12-03
forum: Hardware
---

### Post by Raikiri on 2012-12-03
Hi guys.

I just got hold of a laptop, Acer aspire one 751h which is in pretty decent shape.  It had windows on it but I wiped the drive and installed ubuntu on it.  After installing, it felt like XP on an old and poorly maintained PC, everything was so sluggish it was basically unusable.

That laptop has 1Gb of RAM.  I have an older aspire one, the zg5 version and it handles ubuntu pretty well, although it has 1.5Gb RAM.

I tried installing 11.04 on it after seeing 12.10 was sluggish because I had it lying around anyway and 11.04 seemed a lot faster.  Could there be anything behind this like missing drivers etc?

Thanks

---

### Post by mikewhatever on 2012-12-03
Aspire One 751 is a GMA500 netbook, at least according to [a review]("http://www.notebookcheck.net/Review-Acer-Aspire-One-751-Mini-Notebook.17809.0.html") I've googled up. That particular Intel's chipset lacks proper Linux support. There is no 3d acceleration, which is required by 12.10, and that is why it's slow. 12.04 should be a bit faster with Unity2d.

---

### Post by ahallubuntu on 2012-12-03
> **Raikiri said:**
> Hi guys.

I just got hold of a laptop, Acer aspire one 751h which is in pretty decent shape.  It had windows on it but I wiped the drive and installed ubuntu on it.  After installing, it felt like XP on an old and poorly maintained PC, everything was so sluggish it was basically unusable.

I have an AO751h I bought three years ago.  It's a Netbook not a "laptop" FYI.  It's got an Intel Atom CPU in it, so it's going to be very, very slow, no matter what you do.

I have 11.04 on mine, too.  (11.04 is no longer supported, unfortunately.)  To get 11.04 to work at correct screen resolution requires some hacks (but they are well known and packaged - google for more info).  Even 11.04 has issues on it.  It will freeze coming out of suspend about 1/5 times, then you have to hard shut down and reboot.  Annoying, but for a travel laptop it is usable.

I may play with 12.04 on it - but you have to dig up the GMA500 tricks to make it work right, I hear.  I'm not sure I'll even bother.  This old netbook has been slow with every OS I've tried on it (XP was slow too).  And with all of the GMA500 issues, I don't think it's worth more of my time.

For what it's worth: I upgraded the RAM to 2GB and the wireless card to an Intel 5100 802.11n card - both very easy to do from the bottom.  Because it's a larger netbook, these components aren't buried under the keyboard.  Hard drive easy to swap out too.  But I probably wouldn't spend much money to upgrade those things now.  They made more sense when it was pretty new.

---

### Post by Raikiri on 2012-12-04
> **ahallubuntu said:**
> I have an AO751h I bought three years ago.  It's a Netbook not a "laptop" FYI.  It's got an Intel Atom CPU in it, so it's going to be very, very slow, no matter what you do.

I have 11.04 on mine, too.  (11.04 is no longer supported, unfortunately.)  To get 11.04 to work at correct screen resolution requires some hacks (but they are well known and packaged - google for more info).  Even 11.04 has issues on it.  It will freeze coming out of suspend about 1/5 times, then you have to hard shut down and reboot.  Annoying, but for a travel laptop it is usable.

I may play with 12.04 on it - but you have to dig up the GMA500 tricks to make it work right, I hear.  I'm not sure I'll even bother.  This old netbook has been slow with every OS I've tried on it (XP was slow too).  And with all of the GMA500 issues, I don't think it's worth more of my time.

For what it's worth: I upgraded the RAM to 2GB and the wireless card to an Intel 5100 802.11n card - both very easy to do from the bottom.  Because it's a larger netbook, these components aren't buried under the keyboard.  Hard drive easy to swap out too.  But I probably wouldn't spend much money to upgrade those things now.  They made more sense when it was pretty new.

Yeah, yeah, a netbook is still a laptop of sorts but alright.

11.04 seems to be usable right now on the "classic, no effects" setting but it just looks ****, probably the resolution as you say.  I'm just annoyed there's nothing better I can do with this perfectly functional netbook, maybe I was too quick to wipe windows XP off it because dare I say it, it was running pretty well.

Are there any other options I can look at to make use of it?  If the chipset isn't supported then are all linux distros a waste of time?  What about android?

---

### Post by Peter Maunder on 2012-12-04
I have an Aspire One D150 Intel Atom 1GB Netbook running Linux Mint 13 Mate.  Screen quality seems fine, I have it set to 1024 x 600. Not as fast as my other systems with just the 1 GB.

---

### Post by 2F4U on 2012-12-04
> **Raikiri said:**
> Yeah, yeah, a netbook is still a laptop of sorts but alright.

11.04 seems to be usable right now on the "classic, no effects" setting but it just looks ****, probably the resolution as you say.  I'm just annoyed there's nothing better I can do with this perfectly functional netbook, maybe I was too quick to wipe windows XP off it because dare I say it, it was running pretty well.

Are there any other options I can look at to make use of it?  If the chipset isn't supported then are all linux distros a waste of time?  What about android?

If it doesn't have to be Gnome or Unity, you could try Xubuntu or Lubuntu. Both are intended for less powerful hardware and will probably run very well on your machine.

---

### Post by mikewhatever on 2012-12-04
> **Raikiri said:**
> Yeah, yeah, a netbook is still a laptop of sorts but alright.

11.04 seems to be usable right now on the "classic, no effects" setting but it just looks ****, probably the resolution as you say.  I'm just annoyed there's nothing better I can do with this perfectly functional netbook, maybe I was too quick to wipe windows XP off it because dare I say it, it was running pretty well.

Are there any other options I can look at to make use of it?  If the chipset isn't supported then are all linux distros a waste of time?  What about android?

So, what exactly do you want to do with it? Other *buntu 12.10 flavors that don't require 3d should run considerably faster, as well as 12.04 flavors. It's not going to work for games or HD video, but other then that, I wouldn't say there is no use for it. AFAIK, there is no version of Android for the GMA500.

---

