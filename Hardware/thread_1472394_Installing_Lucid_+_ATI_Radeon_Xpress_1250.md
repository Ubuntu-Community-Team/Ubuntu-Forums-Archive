---
title: "Installing Lucid + ATI Radeon Xpress 1250"
date: 2010-05-04
forum: Hardware
---

### Post by Mobydesu on 2010-05-04
Hi all,

I'm trying to install Lucid on a laptop with ATI Radeon Xpress 1250 using a Live CD, without success. After the "keyboard = human" screen, everything goes blank, but the CD is still runs, until it spins to a stop. No flashing cursor or terminal.

Is there a way I can install with Live CD? I've been told by a friend that it might have to do with graphics drivers.

Thanks in advance!

---

### Post by agm1101 on 2010-05-05
I am having exactly the same problem. I tried all the different F6 options - nomodeset, noacpi, noapic, etc. - still does not work. I have been using hardy on this same laptop without any problems for the last year and half - everything working great. I was really looking forward to upgrading to this LTS release, but it won't even startup the livecd. Can someone suggest options please? Thanks.

---

### Post by partymetroid on 2010-05-05
I don't really know how to help, but I guess I can point you to this Ubuntu Wiki page: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver).  It seems that your card is indeed supported by the open source driver quite well... which is what Ubuntu will generally use.

The only other advice I can give you is to try to install with the Alternate Install CD... but that might be pointless, as you're having problems with the LiveCD's video. :?

Sorry I can't be of much else help! :(

---

### Post by agm1101 on 2010-05-08
> **partymetroid said:**
> I don't really know how to help, but I guess I can point you to this Ubuntu Wiki page: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver).  It seems that your card is indeed supported by the open source driver quite well... which is what Ubuntu will generally use.

The only other advice I can give you is to try to install with the Alternate Install CD... but that might be pointless, as you're having problems with the LiveCD's video. :?

Sorry I can't be of much else help! :(

I know my driver is supported, because I have been running Hardy Heron (8.04) since more than a year without any problems. I had been waiting for the LTS release thinking that it would "just work", but apparently, thats really not true. Something that works, can "just break". 

Searching on the internet, looks like a bunch of people have the same problem with the same driver. Using nomodeset solved it for a lot of people, but it didn't for many of us.

Hope someone somehow finds something to get around it.

---

