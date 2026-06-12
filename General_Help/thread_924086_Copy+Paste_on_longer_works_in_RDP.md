---
title: "Copy+Paste on longer works in RDP"
date: 2008-09-19
forum: General Help
---

### Post by jbt on 2008-09-19
Hi,

I'm running Gutsy.

I have been using RDP for a few weeks, and it was working great until today.

This morning, Update Manager had an update for RDP, which I installed, but now cut+paste no longer works from the remote desktop to my local desktop.

1) How do I report this problem ?

2) Can I rollback RDP to the previous version ?

Thanks
JohnT

---

### Post by snakyjake on 2008-10-26
I have the same problem.  I'm running Hardy Heron and connected from Linux to Windows XP via RDP.  Copy/paste does not work.  I've tried ctrl keys, right clicks, and edit menu...none of the ways to copy/paste work.

Any ideas?

---

### Post by iannoel on 2008-11-09
> **snakyjake said:**
> I have the same problem.  I'm running Hardy Heron and connected from Linux to Windows XP via RDP.  Copy/paste does not work.  I've tried ctrl keys, right clicks, and edit menu...none of the ways to copy/paste work.

Any ideas?

I have the same problem! (somebody else?)

I try to select in windows -> then click over selection -> drag&drop to the paste region.

I try with Terminal Server Linux and get the same result.

Hate it!

Then have a new problem, the CapsBlock don't works!

(My English Sucks! shhhhhh)

---

### Post by Tobbera on 2008-12-21
Same problem here. Any solution?

---

### Post by Tobbera on 2008-12-21
SOLUTION: Use RDP instead of RDPv5. Seems that RDP is using RDPv5. RDPv5 is using RDPv4.

---

### Post by herend on 2009-02-11
solution: to make it work with RDPv5

remote desktop/ on tab "speed"
check the "hide decoration of window management" 
(my ubuntu's language is not english, so it can be different :))

Unbelieveable, but copy/paste works. :)

---

### Post by deadguy on 2010-05-04
From the manpage for rdesktop:

[INDENT]-5     Use RDP version 5 (default).[/INDENT]

Seems wrong though, because copy/paste works for me ONLY with `rdesktop -5`.  Could this be a documentation bug?

---

