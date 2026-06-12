---
title: "Touchpad / Pointer Freeze after copy/paste"
date: 2006-08-26
forum: Hardware &amp; Laptops
---

### Post by JoryC on 2006-08-26
I am running Breezy on a Dell Inspiron 3800 (600mHz pIII, 256MB RAM) and I am experiencing a mouse trackpad problem.

(I previously had Dapper installed and I had the same problems)

When I cut, copy, or paste text using keyboard shortcuts the pointer freezes for a little bit (about 15 seconds) but I can still type and generally use the keyboard for commands. It seems to only happen with keyboard shortcuts, not the menu equivalents.  

Is it a disk access problem? A driver configuration issue?

Has anyone had this problem before? i searched the forums and saw people seemed to have the opposite problem, (everything but freezes until trackpad is moves) but not my issue.

Thanks in advance for any help from a total Ubuntu noob.

---

### Post by spangemonkee on 2007-01-21
I have the same issue with my Inspiron 4000 running Dapper 6.06 LTS. The only solution I can find, besides not using the CTRL key, is to run this in a shell:

sudo rmmod psmouse
sudo modprobe psmouse

it restarts the mouse.. it's quite annoying.

---

