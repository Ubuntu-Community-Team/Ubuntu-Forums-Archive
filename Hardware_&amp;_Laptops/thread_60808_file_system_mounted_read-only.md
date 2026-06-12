---
title: "file system mounted read-only"
date: 2005-08-29
forum: Hardware &amp; Laptops
---

### Post by Athelek on 2005-08-29
Both Ubuntu and Kubuntu have thrown up the same error - during normal use it will [after an hour or two] suddenly remount my Maxtor 120 GB hard drive] read only. 

I'm currently running Ubuntu, but Kubuntu was having the same problems, which is the reason I swapped, in a vague hope that it'd sort out. Kubuntu also gave a more detailed error message - "Could not start process Unable to create io-slave File system mounted read-only".

And would then stay read only until I rebooted and ran fsck, which reports stuff like:

"Inodes that were part pof a corrupted orphaned link list found. Fix <y>?"
and
"Block bitmap differences [and then a large string of numbers I have written down] Fix <y>?"

To which I've always answered yes, since I don't know any better. 

This is completely new to me, and the only thing I can think I've changed between not having the problem and now is replacing the motherboard [broken BIOS]. Any ideas on how to fix this? If it can be fixed...

---

### Post by pmjdebruijn on 2005-08-29
Hi,

Well this sounds like a classic case of disk rott... put shortly your harddisk is most probably dying.

Or it might be a rotten IDE cable!

Anyway to find out, try installing 'smartmontools' with Synaptic. Then open a Terminal, and type:
```
sudo smartctl -a /dev/hda
```

Look for something like this:
**SMART overall-health self-assessment test result: PASSED**

This will tell you whether your harddisk is failing or not!

Regards,
Pascal de Bruijn

---

