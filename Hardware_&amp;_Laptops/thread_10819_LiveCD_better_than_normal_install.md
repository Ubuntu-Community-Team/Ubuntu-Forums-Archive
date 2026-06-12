---
title: "LiveCD better than normal install"
date: 2005-01-11
forum: Hardware &amp; Laptops
---

### Post by cmoir on 2005-01-11
Why is it that the LiveCD, which is meant to be a preview of the real thing, works better than the real thing?

I've installed Ubuntu on two completely different systems. On both the full install has failed to correctly identify hardware that the LiveCD does correctly identify and configure. The live CD also appears to do all this in about a fifth of the time it takes the main install.

Specifically, on both systems the full 4.10 install failed to detect my NICs, or in one case detected it but failed to configure it.  On both systems the LiveCD correctly identified and configured the monitor but on the full install I can't get any more than 60Hz refresh (it hasn't identified the fact that this monitor can do 85Hz at 1600x1200 easily (the live CD defaulted to that setting)).  3com network card and Radeon video on otherwise standard Dell boxes.

I'm a relative newbie but I think the LiveCD is potentially misleading people. Can't the full CD install be as good as the LiveCD?

Lastly, other Linux guys have told me to configure my network card by settings in  /etc/modules.conf but no such file exists. Is this a debian thing? If so where exactly are driver files configured?  (I know that in one case the card is not selecting the correct network media interface and this can be forced in a config option).

Lastly, lastly, I have a load of comments on bugs / documentation inaccuracies and such. I really want to help improve Ubuntu, but I'm not sure where best to post this feedback where it's most likely to get acted upon. Forums, FAQs, mail lists, bugzilla, what?

Thanks,

---

### Post by jdong on 2005-01-11
The LiveCD uses Knoppix hardware detection routines.

This is going to change with Hoary, which will use Debian's discover routines.

---

### Post by cmoir on 2005-01-11
But doesn't the current main install use Debian hardware detection already?  The Knoppix ones appear to work better. So isn't this a step in the wrong direction, moving the liveCD to inferior hardware detection, or am I missing something here?

---

### Post by jdong on 2005-01-11
Debian's detection is going to improve. (Knoppix detection routines were based off RedHat 7.1's Kudzu, so be careful what you're recommending!)

Hoary has a newer installer and discover package.

---

