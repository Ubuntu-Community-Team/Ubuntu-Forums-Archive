---
title: "HDD Failure, Rysnc question."
date: 2011-02-04
forum: Hardware
---

### Post by tnt_tnt on 2011-02-04
Hi,

Preamble:

I've got a HDD whose SMART data shows 67 bad sectors. I have run badblocks and this has been confirmed.

I am going to be RMA'ing the HDD as it is still under warranty.

This problem was brought to my attention when running a rysnc. I got this output for four files:

```
ERROR: "[the file location]" failed verification -- update discarded.
```

Question:

I can obtain the 4 files that got this error code from previous backups, but is all the other data that rysnc backed up safe?

Or should I run a dd rescue to extract data?

It is a 1.5 TB HDD so I could do without running dd rescue, especially as it has bad sectors that would slow it down...

Thank you.

PS Sorry if I have re-posted this question, I had originally posted it in the "Absolute Beginner Talk".

PSS How can I delete/move this thread as I posted it in the wrong section?

---

