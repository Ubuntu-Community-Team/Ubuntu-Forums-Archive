---
title: "Hibernate/resume"
date: 2009-05-15
forum: Hardware
---

### Post by PACSFerret on 2009-05-15
Hi. (Ubuntu JJ) I recently upgraded the memory in my laptop and found I couldn't hibernate as there wasn't enough space in the auto-generated swap area.  No probs....I cleared enough contig space, set up more swap and changed the required lines in fstab.  Works so far - new swap kicks in on reboot (now this isn;t the main question I have but should there be something that watches for that scenario?  It wouldn't be a uncommmon circumstance & the only reason I found out there was something amiss was when I closed the lid and put it the bag expecting it to hibernate & found it overheating to the point of being dangerous;))

BUT..  now attempting to hibernate I'm getting an error message "cannot find swap device".  I  changed the UUID also in /etc/initramfs-tools/conf.d/resume but no progress.  Is there somewhere else I need to change?

---

