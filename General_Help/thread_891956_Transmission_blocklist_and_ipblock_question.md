---
title: "Transmission blocklist and ipblock question"
date: 2008-08-16
forum: General Help
---

### Post by stormtrooprdave on 2008-08-16
I have transmission 1.32 and have updated the blocklist.  It says 222000 blocked.  If I am using this is it still beneficial to have ipblock running as well or am I just duplicating processes?

---

### Post by stormtrooprdave on 2008-08-18
bump

---

### Post by MakLeod on 2008-08-21
/bump

Would also like to know this answer.

---

### Post by meonkeys on 2008-08-24
Blocklist question, hopefully not too far offtopic.

I tried to update my blocklist by navigating to [FONT="Courier New"]Edit -> Preferences -> Peers[/FONT] and clicking [FONT="Courier New"]Update Blocklist[/FONT]. After doing so, my only option was to [FONT="Courier New"]Ignore the 0 blocklisted peers[/FONT]. Zero? That couldn't be right.

I manually downloaded the level1 blocklist from bluetack, uncompressed it with [FONT="Courier New"]gunzip[/FONT] and placed it in [FONT="Courier New"].config/transmission/blocklists/[/FONT].

After doing so (while transmission wasn't running), I can now [FONT="Courier New"]Ignore the 1,526,675 blocklisted peers[/FONT]. Wow, that's a lot.

I noticed the level1 blocklist was 12 megabytes, so I compressed it with gzip to see if transmission could still read it. Strange, transmission then seemed to think that only about 450,000 peers were on the blocklist.

Anyone know if the blocklist must be uncompressed for transmission to properly use it?

---

### Post by rockstar1o9 on 2008-09-08
bump

---

### Post by kpkeerthi on 2008-09-08
> **stormtrooprdave said:**
> I have transmission 1.32 and have updated the blocklist.  It says 222000 blocked.  If I am using this is it still beneficial to have ipblock running as well or am I just duplicating processes?

If you already have ipblock, then you won't need to add a block list to transmission also, since ipblock applies the filter system-wide. You only need add the blocklist you are using in transmission to ipblock and turn the feature off in transmission.

If you need the filter applied to your bittorrent traffic alone, then you won't need ipblock. Turn off ipblock.

Hope it is clear.

---

### Post by Terc on 2009-01-12
/bump
Was this issue ever resolved?

I just walked a friend through enabling blocklists today.  I'd like to be sure it's working for them.

---

### Post by Hideaki on 2009-04-30
You only need one block-list. But Transmission only applies it's block list to bitttorrent traffic, so if you want it to apply to more than just bittorrent traffic then use ipblock, turn off the feature in Transmission. Otherwise, use the feature in transmission and turn of ipblock.

---

