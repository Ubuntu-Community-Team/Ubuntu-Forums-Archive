---
title: "&quot;Unable to find a medium containing a live file system&quot; Sony Vaio PCG-N505SN"
date: 2009-11-09
forum: Hardware
---

### Post by kristan66 on 2009-11-09
Hi there

I want to install xubuntu on my old Sony VAIO PCG-N505SN;  I have tried both the Live Desktop and main install, but it always gets to a point where it says "Unable to find a medium containing a live file system"

I *believe* this may be because there are issues with the PCMCIA CD-ROM drive... The laptop boots from that drive OK.

When I add boot options, do they have to appear after the "--"  ?
I have tried boot options:
nopcmcia 
hw-detect/start_pcmcia=false
debian-installer/probe/pcmcia=false

I have tried putting them after the --, and before it... I have never used Linux before, so it anyone had any suggestions that would be great.

It may have nothing to do with the PCMCIA CD-ROM external drive, but there are lots of posts on the internet suggesting this may be the case.


thanks for your help
Kris

---

### Post by glenwpetrie on 2009-11-18
I found an old reference to a similar vaio; check it out.
 
[http://ubuntuforums.org/archive/index.php/t-386152.html](http://ubuntuforums.org/archive/index.php/t-386152.html)

---

