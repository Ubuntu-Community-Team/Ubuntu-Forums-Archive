---
title: "HP Pavillion tx2000 - No sound - Ubuntu 9.04"
date: 2009-07-13
forum: Hardware
---

### Post by duph on 2009-07-13
Hi!

I have a HP Pavillion tx2000 and I'm running Ubuntu 9.04 and I have the same problem as in this topic: [http://ubuntuforums.org/showthread.php?t=972552](http://ubuntuforums.org/showthread.php?t=972552). (Reposted as new topic because the other one says [SOLVED]. Hope that's ok..)

I've tried adding the following as the last line to "alsa-base.conf", but neither of them seem to work after I reboot:

options snd-hda-intel index=0 model=toshiba position_fix=1
options snd-hda-intel model=hp

I've also reopened the file to verify that it's actually been saved correctly.

Any suggestions as to what I might do to correct the problem?


I also got this link from the Sound Troubleshooting guide, if it's any help: [http://www.alsa-project.org/db/?f=d5703efd92820a394650c66650ef6cb0db5b2648](http://www.alsa-project.org/db/?f=d5703efd92820a394650c66650ef6cb0db5b2648)

---

### Post by wojox on 2009-07-13
snd-hda-intel: index=0 model=toshiba position_fix=1
snd-hda-intel: model=hp

Added colons after intel.

---

### Post by duph on 2009-07-13
Never mind.. It all of a sudden started working.

[@_@ ]

---

