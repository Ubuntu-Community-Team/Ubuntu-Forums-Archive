---
title: "Acer Aspire One 512mb - pre-buying advice?"
date: 2009-05-11
forum: Hardware
---

### Post by frankwakeman on 2009-05-11
A shop near me in Kent, England is selling the Acer Aspire One netbook, in white, for £149.  It has the Linpus OS on it and my broadband method is a Vodafone 3G dongle which I run well and simply with Network Manager.

How viable will it be to get Ubuntu 9.04 installed instead (full version or Netbook Remix, which I haven't properly read up about yet) or possibly Xubuntu 9.04 if advised?  What problems will there be, and how quickly and simply a now fairly competent Ubuntu installer like me get the Acer Ubuntu'd up.  If I'm honest if they'd had the XP version I'd have bought it already.

Are there any hardware failure surprises involved with this model, e.g. audio?  Mic and headphones.  (I might want to record guitar on it with Audacity.)

I have an external USB CD drive and a copy of the Canonical Ubuntu 9.04 CD.  Will the boot-up from this be a straightforward BIOS choice or is it plainly prevented somehow?  I'm being cautious because though the shop has already apparently had two of these returned, I would think because of the Linux confusion, I don't fancy having to negotiate this with the shop's staff, I'm a bit of a quiet bloke.

I use a 1.3 ghz Fujitsu desktop pc with the current Ubuntu, which I find not ideal but still very bearable speed-wise and imagine the Acer Aspire One will therefore be more than bearable at 1.6 ghz?

Any other pointers and info is appreciated.  

Thanks.

---

### Post by coffeecat on 2009-05-11
I've installed the Jaunty NBR to my Asus EeePC and I'm very pleased with it. I have no experience of the Acer, but I can give you a few pointers. First, don't let anyone tell you 512MB RAM is not enough. Jaunty NBR runs fine in 512MB RAM on my Eee, **and** with no swap partition (because it's a SSD).

Next, you don't install Jaunty NBR from a CD. [Here's the download page]("http://www.ubuntu.com/getubuntu/download-netbook") from which you get an .img file, not an .iso. Then you write the .img to a USB flash drive - [HowTo here]("https://help.ubuntu.com/community/Installation/FromImgFiles").

Also, [this community documentation page]("https://help.ubuntu.com/community/AspireOne") about Ubuntu on the Aspire One might be useful. And, [the AspireOne forums]("http://www.aspireoneuser.com/forum/") might give you some more information.

Last thing - on the Asus Eee there's a bad issue with mouseover on the NBR interface. I don't know whether that's true with Jaunty NBR with the AspireOne, but if you get this, have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1136599"), particularly post #5. If you download and install that special kernel (at least with the Eee) the issue goes away.

---

