---
title: "Migrating from Ubuntu to Kubuntu: FF and TB"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by galvao on 2009-05-24
Greetings.

I've just switched from Ubuntu 8.10 to Kubuntu 9.04 and I was wondering if it would be possible to just copy my profiles from Firefox and Thunderbird directly into my ~/.mozilla/firefox and ~/.mozilla-thunderbird folders.

I know this practice is usually not recommended, but since the versions of both are identical (I've always kept both updated in my Ubuntu 8.10 installment) I was thinking that logically this should work with no problems, right?

I mean, OK, I have no problem in downloading and installing the extensions and themes for both, but things like mailboxes should be OK, right?

In case I'm wrong, which would be the right way to do it?

TIA,

---

### Post by tommcd on 2009-05-24
I would think that it would be ok. You can always backup your .mozilla directory before you copy your profiles over, just in case anything goes wrong.

---

### Post by presence1960 on 2009-05-24
That is exactly what to do. If you start FF or TB and your settings don't come up, close the program. Open a terminal and run ```
firefox -profilemanager
``` for FF and ```
thunderbird -profilemanager
``` for TB. Click create and choose a new name for your profile.Follow the prompts. You will choose the profile folder you copied to your respective config folder (.mozilla & .mozilla-thunderbird). After creation it is safe to delete the Default profile

---

### Post by galvao on 2009-05-25
Thanks, guys!

---

