---
title: "Opinions/experience using Highpoint Rocket 640L for mdraid on Ubuntu Precise Server"
date: 2013-01-20
forum: Hardware
---

### Post by liquidonline on 2013-01-20
Hello all,

I have a server performing the function of central fileserver among other tasks.  I have a total of 8 disks + OS disk in there using mdraid to setup a mix of raid5, raid10 and raid1 depending on requirements.  My current choice of add-on HBA is giving me a hard time.  Given I will use mdadm, I am trying to avoid tossing money into a HW raid card just to gain the (perceived?) stability they'll bring.  I just need a solid HBA I can use in conjunction with on-board sata, or an HBA that I can run two of with no issues, and boot off them.

In the past, I've setup FreeBSD servers and noted that whenever an unsupported "raid" controller was in play, typically I'd still be able to access disks standalone, but not benefit from any raid functionality (which was just fine, I'm as much a fan of gmirror/gstripe as mdadm ;) )  This was the case with the captioned HBA, until it was patched, and later committed to 9.1.  I'm just having a really hard time finding any information to suggest (or better still validate) that the card will function as a simple HBA in recent versions of Ubuntu.  Can anyone chime in on that?

If this one is not, but the RocketRaid version (the one that has the "better" fakeraid) is better supported, please do share your experience as well.

Thanks!

---

