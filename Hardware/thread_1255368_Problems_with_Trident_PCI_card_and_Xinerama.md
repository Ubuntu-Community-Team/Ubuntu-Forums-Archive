---
title: "Problems with Trident PCI card and Xinerama"
date: 2009-09-01
forum: Hardware
---

### Post by Cjack1975 on 2009-09-01
((Not sure about correct Category for posting this, feel free to move this topic))

I've been an Ubuntu/Xubu user since Dapper, currently running Jaunty, and occasional Linux user since RedHat 4. 

I've recently composited two machines into one, with much success, and only one failure.

I'm trying to get an old PCI vid card (Trident 9660) enabled as a second display. The primary use of this will be as Xine out, and maybe system monitors for quick references.

This is my first attempt at this feat. I am understanding that I will need to edit the /etc/xorg.conf. and add a second Screen, Monitor, and Device sections, and add a ServerLayout Section that enables Xinerama.

I have tested that everything works (changing my PC's BIOS to Boot with the PCI card)

But upon asking X to reconfig and enable the Multi-Head. the X log file says it cannot find the VBE BIOS for the Trident card, so Ubu runs at low color / res unless I run with my previous X config file.

Suggestions? 

Much Appreciations.

Christopher

---

