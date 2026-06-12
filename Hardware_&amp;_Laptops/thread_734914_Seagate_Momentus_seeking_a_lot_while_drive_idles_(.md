---
title: "Seagate Momentus seeking a lot while drive idles (PS, apm=254)"
date: 2008-03-25
forum: Hardware &amp; Laptops
---

### Post by Tripwirecc on 2008-03-25
I have this new laptop with a Seagate Momentus 7200.2. Obviously, this thing did the head parking thing, which is fixed.

Now, when the drives idles (means no IO caused by Linux), it regularly starts doing head seeking noises, which stop by themselves or when you cause IO, but restart every while after idling. SMART data doesn't indicate anything wrong, smartctl induced selftests pass, too. It doesn't do that when APM in enabled, since it parks the heads first.

Now I've read that Seagate has a patent on something called Seek to Increase Reliability (or STIR). It's about making the heads seek to prevent the head of resting above a single track and make it heat up.

Since this feature seems to have been renamed and not be mentioned anywhere except in a few very old data sheets, I don't know if it's a standard feature or not. Seagate tech support replies with a canned answer, suggesting stupid things, too (like powering the drive without SATA cable attached, which makes APM kick in instead), instead of clarifying whether this is an assumed drive feature.

So, what could it be? Any other Seagate Momentus owners noticing the same? Or is my drive faulty (but not faulty enough to trigger Seatools or anything)? I'm hoping it's just the STIR thing, considering it doesn't do it when APM is enabled.

Thanks.

---

### Post by Tripwirecc on 2008-03-25
Bump for the night crew.

---

