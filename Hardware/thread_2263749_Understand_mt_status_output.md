---
title: "Understand mt status output"
date: 2015-02-03
forum: Hardware
---

### Post by vangend.robert on 2015-02-03
I have a server running Ubuntu 12.04 with a DELL LT02 tape drive. 

Everything works OK, I can backup / restore etc.

I am curious however. How do I interpret the results from "mt -f /dev/nst0 status"? 

I get these results, but have no idea what this means.:

"mt -f /dev/nst0 status"
drive type = 114
drive status = 1107296768
sense key error = 0
residue count = 0
file number = 0
block number = 0

For example, what the heck does "drive status = 1107296768" mean. I have checked "man mt", and googled, but can't find any reference to the meaning of the output of the status command.

Anyone have a link for a reference guide or some feedback please.

---

