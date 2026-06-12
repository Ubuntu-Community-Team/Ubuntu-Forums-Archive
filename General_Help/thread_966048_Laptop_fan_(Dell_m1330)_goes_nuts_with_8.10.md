---
title: "Laptop fan (Dell m1330) goes nuts with 8.10"
date: 2008-11-01
forum: General Help
---

### Post by Zeedok on 2008-11-01
Myself, and at least one other Dell m1330 laptop owner ([http://ubuntuforums.org/showthread.php?p=6078522#post6078522](http://ubuntuforums.org/showthread.php?p=6078522#post6078522)) have had problems with the fan in our laptop after upgrading to 8.10.  I thought I'd open up the problem to 'General Help' to see if this is a Dell specific issue, or a laptop generic issue.

My fan comes on and off repeatedly (like 5 secs on, 1 sec off, 5secs on etc) and it's really annoying.  When I upgraded, I had gkrellm installed, so I experimented with different fan trigger settings, but it didn't seem to make any difference.  I removed i8utils and gkrellm and the fans keep keeping on . . .

I just realised that I still have "i8k force=1" listed in my /etc/modules file - I'll try removing that to see if the issue is resolved.

---

### Post by soulnafein on 2008-11-06
I have the very same problem with the same laptop model.
Suggestions?

---

### Post by Zeedok on 2008-11-06
I found a couple of other threads tackling this issue on the Dell support section of the forum.

Upgrading the bios to the latest version (A12) solved the issue.

Good luck.

---

### Post by pognonec on 2009-09-28
I found a (weird) solution: in system/administration/harware drivers:
Shift from NVIDIA version 180 to NVIDIA version 173.
Et voilà!
Quiet again :-)

---

