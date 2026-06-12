---
title: "Sound works when it &quot;feels&quot; like it"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by iPLAYwithFIRE on 2007-05-04
Ok, I don't want to sound like a complete idiot.  I promise I didn't just post without researching it first.  Only to google "sound not working" along with "ubuntu" - turns up a lot of results haha.  So I thought I had it figured out....

I typed in:
```

sudo asoundconf list

```

It gave me a list in this order:
ICH5
Live

I did that for when it didn't work and when it does work....
When it does work the list is in this order:
Live
ICH5

so I thought if I use:
```

sudo asoundconf set-default-card Live

```
then it would work.  And it did, for a little while haha.  Now it doesn't work at all.  Now when I pass that in it doesn't even effect the order that the sound is listed in.  I don't think it's setting Live as the default card.  Is there a way to pass it in to change it permanently?

Like I said, it seems to work when Live is first in the list.  But, I haven't had ENOUGH trial and error to determine it as fact.

---

