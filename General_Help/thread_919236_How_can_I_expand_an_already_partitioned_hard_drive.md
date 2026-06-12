---
title: "How can I expand an already partitioned hard drive?"
date: 2008-09-13
forum: General Help
---

### Post by JohnParker on 2008-09-13
Right now I have 2 partitions, one with ubuntu and one with XP, But the ubuntu partition is only about 10 gigs, is there any way I can expand it to about... 80? Its a 250 Gig HD. I do have partition magic and gparted.

---

### Post by caljohnsmith on 2008-09-13
> **JohnParker said:**
> Right now I have 2 partitions, one with ubuntu and one with XP, But the ubuntu partition is only about 10 gigs, is there any way I can expand it to about... 80? Its a 250 Gig HD. I do have partition magic and gparted.

Sure, just use gparted. Of course you'll have to run gparted from your Live CD so your HDD is not mounted when you operate on it. If XP is taking up all the rest of the space on your HDD, you will of course have to shrink it before giving Ubuntu more room.

---

### Post by benerivo on 2008-09-13
And if you do shrink the XP partition, then I would recommend booting XP beforehand and defragmenting twice (because more is better).

---

