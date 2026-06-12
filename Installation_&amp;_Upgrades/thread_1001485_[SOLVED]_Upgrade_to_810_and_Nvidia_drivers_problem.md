---
title: "[SOLVED] Upgrade to 8:10 and Nvidia drivers problem"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by sanford55 on 2008-12-04
Hi everyone.  Thanks for past help with problems.  I am trying to upgrade from 8.04 to 8.10 on a dual boot Dell machine and I get the following message.  "This computer is currently using the NVIDIA 'nvidia' graphics driver. No version of this driver is available that works with your video card in Ubuntu 8.10."  It says "Upgrading may reduce desktop effects, and performance in games and other graphically intensive programs."  My questions are these.  First, is this a permanent problem, or can I expect 8.10 to support these graphics drivers in the future?  Second, if I proceed with the upgrade, how serious will the problem be and can I easily roll back to 8.04?  I am not a gamer but do watch some movies on my machine.  Third, are there any other solutions to this sort of problem?  Thanks in advance for help.  Sanford

I have more information.  I have a gforce4 mx 420 graphics card.  Also, I found in the release notes for 8.10 a comment about nvidia legacy support that I do not understand.  It says "GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration."  Does this mean that if I upgrade, it will automatically include a "free nv driver," but one that just does not have 3D acceleration?  I can live with that! Or do I have to get this upgraded nv driver elsewhere, from nvidia.  Thanks again.  Sanford

---

### Post by DieB on 2008-12-04
as far as i understand it: the system will use the free nv-driver instead of the propietory one.

so no 3d effects for u (shadows behind wndows ...).

BUT STILL IT IS A PLEASURE TO USE UBUNTU

---

### Post by falcon61102 on 2008-12-04
Yes, when you upgrade Ubuntu will install the legacy driver.  The new nvidia graphics chips use a restricted driver and your chip currently isn't compatible with those drivers.  All the release notes are saying is that until they come out with a new driver, Ubuntu will use the legacy ones.

---

### Post by Happypants on 2008-12-04
I've had lots of problems with my Nvidia drivers in the past.  This link tells you exactly what I did to get around it.  After that they work like a charm.

[http://ubuntuforums.org/showthread.php?t=992293&page=2](http://ubuntuforums.org/showthread.php?t=992293&page=2)

---

