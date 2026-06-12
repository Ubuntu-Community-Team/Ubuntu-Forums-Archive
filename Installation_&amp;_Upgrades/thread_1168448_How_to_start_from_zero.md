---
title: "How to start from zero?"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by emongev on 2009-05-24
I had 8.04 on a root and a home partition.

Now,

i wanted to install jaunty and have all reset from zero (no apps i installed previously etc) so i installed over my root partition, yet, i still have all the apps i had, dunno if it has something to do with the fact that i kept the same home partition, and if it were, can someone direct me to how i can reset it, without losing the info i have in my desktop for example.

thanks in advance =)

---

### Post by Elfy on 2009-05-24
If you had a seperate home then all the coinfigs would have remained. You can remove the configs from your home - open home then do Ctrl+H - all the hidden folders, those folders starting with a .  are where the configs are.

---

### Post by dandnsmith on 2009-05-24
The '*installed over*' suggests that the previous root content wasn't removed.
If that is indeed the case, then one thing to have done might have been to format the root partition (if it was separate). OK, the settings might be there in the /home, but the apps would usually not be there (even if menu items were)

---

### Post by emongev on 2009-05-24
@forestpixie

i actually just found those, is there no problem with just click-deleteing them?

@dadnsmith

i actually checked the box of "Format?" when installing jaunty, yet like 200 megs remained untouched. how do i format the root partition so it cleans it up totally?

Thanks for the quick answers =)

---

### Post by Elfy on 2009-05-24
> **emongev said:**
> @forestpixie

i actually just found those, is there no problem with just click-deleteing them?

@dadnsmith

i actually checked the box of "Format?" when installing jaunty, yet like 200 megs remained untouched. how do i format the root partition so it cleans it up totally?

Thanks for the quick answers =)

Deleting them is not a problem - when the app starts again it would redo the config files - obviously your bookmarks are in the .mozilla one and your e-mails will be in the configs somewhere - I use tbird so mine are in .mozilla-thunderbird.

The 200Mb you have there apparently untouched is the space root keeps so it can work if the drive becomes full, if you told the installer to format then your original system would have been overwritten.

Going back to your first post - you say "yet, i still have all the apps i had" - which apps are these?

---

