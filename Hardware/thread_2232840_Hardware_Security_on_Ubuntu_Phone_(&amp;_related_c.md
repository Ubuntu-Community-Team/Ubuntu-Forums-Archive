---
title: "Hardware Security on Ubuntu Phone (&amp; related chipset / driver choices)"
date: 2014-07-04
forum: Hardware
---

### Post by Oliver_C on 2014-07-04
I've yet to see much if any discussion about hardware related security and personal privacy on Ubuntu Phone.  Canonical have repeatedly stated their intention to make it a secure and private platform, and have continually expressed a desire to have nothing to do with intelligence agencies, spying or facilitating the work of the former.

Whilst I'm sure they'll do everything they can to make the OS itself as secure and private as possible, the elephant in the room is hardware - namely the modem(s) and their architecture vis a vis the rest of the phone's circuitry, and the software and drivers they use.

For real security or privacy, what's needed are modems with some kind of physical separation from the CPU, and preferably open (rather than closed and proprietary) software and drivers operating them, with no facility for the modem to control the CPU or read and write to memory.

The capitulation and market exit of TI & Ericsson, failure of NVIDIA and good business on Qualcomm's part has handed them a gigantic marketshare of SoCs and mobile chipsets in today's smartphones, with a near monopoly on more expensive models.  However, this is extremely bad for security and privacy, as practically all their solutions have either negligible or no separation whatsoever between modem(s) and CPU, and the modems run completely closed, proprietary software and drivers.  This together with them being a very large US based company makes it practically certain that using a phone (no matter the OS it's running) with their chipsets can never really be secure or private.  As the market leader, Qualcomm aren't likely to change a winning formula, and some of their 'friends' would most likely be very persuasive when arguing against more secure designs or open software / drivers.   Samsung, Mediatek and several smaller operators are still there and AMD will most likely enter the market soon, so all is not lost, but typically their designs do not prioritise security or openess.

Basically, I'd like to know if Canonical has had dialogue with hardware partners along these lines, and whether they will look to prioritise 3rd party support for UP phone images for phones which show more potential, privacy and security wise.  Obviously it'd also be good if we could facilitate some kind of community discussion on the matter, and solicit more missives from Canonical and / or chipset makers and phone OEMs.  Would be lovely to hear Meizu and bQ's (launch partners) thoughts on the matter.

---

