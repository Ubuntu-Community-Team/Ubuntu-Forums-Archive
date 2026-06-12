---
title: "Sharing swap partitions"
date: 2005-12-23
forum: Installation &amp; Upgrades
---

### Post by raghav_p on 2005-12-23
Can it be done?

I am planning to install Fedora (when it hits 5) and am wondering if I would have to create a separate swap partition for it.

---

### Post by elwood_j_blues on 2005-12-23
Of course it can.

Provided that the both "linuxes" do not run *at the same time*, they can have the same swap partition.

You also use "the same RAM" for them, don't you ;)

---

### Post by az on 2005-12-23
If you hibernate (suspend to disk) it writes your ram to the swap.  If you share the swap, you will lose your saved session.

Typically, you hibernate a laptop, but I hibernate my desktop too.  It saves on boot up time.

If you do not hibernate, you will not have a problem.


I can not imagine what would happen if you hibernate Ubuntu and then boot fedora which then tries to wake up from a suspend!

---

### Post by raghav_p on 2005-12-23
So if I understand this correctly, as long as I'm not suspending in Ubuntu and waking up in Fedora (or vice versa) I should be ok? 

(That's of course assuming I can get it to suspend on either.. but that's another story)

---

### Post by az on 2005-12-23
[QUOTE=raghav_p]So if I understand this correctly, as long as I'm not suspending in Ubuntu and waking up in Fedora (or vice versa) I should be ok? 

(That's of course assuming I can get it to suspend on either.. but that's another story)[/QUOTE]


That is correct.  You also should not suspend in Ubuntu and then boot fedora, since that will eat your suspended session.  That is not nice to do and may kill some things like not shutting down properly.

---

### Post by Milflyboy on 2006-03-03
WinXP doesn't hibernate to its swap space does it? It just modifies ntloader to point to some part of the system drive, right? I'd like to have XP and Ubuntu share a swap partition, but no other distros. (Of course at the moment, neither one hibernates correctly, but I do NOT plan to have it stay that way. ;))

Eh...sorry, found thread about this: [http://ubuntuforums.org/showthread.php?t=112073](http://ubuntuforums.org/showthread.php?t=112073)

---

