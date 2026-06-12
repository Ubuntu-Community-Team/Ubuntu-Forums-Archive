---
title: "How to get rid of boot messages"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by GrahamM on 2009-01-03
When I start up Ubuntu, I get pages of lines scrolling by each with [OK] at the end. In the past I had one that said [FAIL] but no longer - that was after I had tried to install an nVidia driver on 8.10 for my TNT2 card.

I have this line in menu.lst:
/boot/vmlinuz-2.6.27-9-generic root=UUID=ef646dc3-ecca-4afa-9236-8646cbf6a986 ro quiet splash all_generic_ide floppy=off irqpoll

which should prevent all that verbose scrolling, I thought!

I don't get any messages on shutdown.

Any way to turn off the messages or is there something that triggers them to come on, like an error of some type?

No big deal, but boot time is quite long.

---

### Post by sofasurfer on 2009-01-03
My last install did not have the boot check(?) or what ever you call those messages. But this install does. I think there is a setting to enable/disable this. I also think that if it is disabled you can enable it at startup by pressing a key.

Not much help am I? 
I'm waiting with you for an answer.

---

### Post by GrahamM on 2009-01-06
> **sofasurfer said:**
> My last install did not have the boot check(?) or what ever you call those messages. But this install does. I think there is a setting to enable/disable this. I also think that if it is disabled you can enable it at startup by pressing a key.

Not much help am I? 
I'm waiting with you for an answer.

Thanks for the post - I still don't have an answer on this. But maybe someone will answer ;)

---

### Post by derouge on 2009-01-06
Ah, duh. Missed that you already had the quiet parameter. Are you sure you're actually booting to the correct kernel, the one with the specified quiet parameter?

---

### Post by Mark Phelps on 2009-01-06
I'm curious about this, too.  Even though I have "quiet" in the boot parms in the Ubuntu stanza, within the last few weeks, Hardy started displaying lots of boot messages. Since I've moved over to Intrepid, I don't get the same problem but whenever I go back to Hardy, the problem returns.

---

### Post by GrahamM on 2009-01-07
> **derouge said:**
> Ah, duh. Missed that you already had the quiet parameter. Are you sure you're actually booting to the correct kernel, the one with the specified quiet parameter?

derouge,

Yes, quiet is included for  the -9 kernel that I am booting (and the second -7 one for that matter). The recovery options do not have it  which is I suppose correct.

And Mark - This is Intrepid I am using. I don't believe that those messages were there after the initial install. They started to appear likely when I had tried to install the nVidia drivers (that will not work in Intrepid). But that was corrected and the messages all say [OK], yet still roll by!

Graham

---

