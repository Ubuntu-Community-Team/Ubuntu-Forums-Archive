---
title: "&quot;resume&quot; versus &quot;cold boot&quot;"
date: 2011-02-02
forum: Hardware
---

### Post by SaintDanBert on 2011-02-02
Can anyone tell me (or direct me to readings other than code) how *buntu Lucid decides to **resume from hibernate** instead of perform a cold boot startup?

"Hibernate" is the short-hand way to say, "suspend to disk."  This is different from "Suspend" or "Sleep" which is short-hand for "suspend to RAM."  NOTE -- The /etc/pm/sleep.d/* scripts use the tokens "suspend", "hibernate" followed by "resume" and "thaw." 

Specifically, I'm asking after power-on, how does *buntu know to accomplish "thaw" processing and restart following "suspend to disk?"

Since hibernate writes the system state into the swap partition, does system start processing test some value over there or is some flag or file written some other place for start-time testing?

I have managed to get "suspend"(sleep) and "resume" working on my laptop. I cannot get "thaw" to work and seek ways to diagnose things?

Merci d'avance,
~~~ 0;-Dan

---

