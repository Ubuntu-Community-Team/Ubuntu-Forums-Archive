---
title: "cannot unmount volume - cdrom drive won't eject"
date: 2008-03-26
forum: Hardware &amp; Laptops
---

### Post by djlosch on 2008-03-26
i just made a fresh 7.10 installation from iso and i've been having problems ejecting cds (i have 2 drives and it happens with both).  i pop the cd in and it mounts fine giving me the cd icon on the desktop.  linux disables the manual eject button on the drive itself, so when i use the right-click eject button, i get a message that an application is still using the device.  i check "ps -ef | grep cd" and there is nothing related to the cd rom drives and this happens right after a fresh boot after solely copying files off the discs. i try manually umounting /dev/cdrom0 and /dev/cdrom1 but it says both devices are busy.  i currently have to reboot just to pop in a new cd and thats just ridiculous.  i was intending on ripping my entire cd collection to disc, but this is a huge barrier.

edit:
this is not the hardy heron bug where the error message says the device cant unmount but still unmounts.  the discs are simply not unmounting at all.

---

### Post by logos34 on 2008-03-26
> **sudo** eject

anything?

---

### Post by kushykush on 2008-03-26
Have you downloaded and updated software?   Have you dowloaded and installed third party software packages?   
System=administration=softwaresources?

When you insert the CD in either drives does it show on the desktop?  What happens if you right click (and choose eject)?

---

