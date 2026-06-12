---
title: "Installation Error"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by floydv on 2009-01-15
Downloaded from two different sites trying to see if the file might be corrupt or something, can not boot Ubuntu when grub starts error "unable to load system description tables" when trying to boot only get a cream colored screen or black, does anyone know of a quick fix to this error?? I am trying to install 8.10 desktop.

My system is windows xp 1GB Ram,,Celeron 2.93GHz,home edition with service pack 3,,primary drive 160GB seagate,,slave drive 160GB Western Digital.

---

### Post by taurus on 2009-01-15
1.  Did you run the checksum to check the integrity of the ISO image?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2.  How fast did you burn the ISO image?

3.  At the initial menu, did you check the cd for defects?

---

### Post by floydv on 2009-01-15
I thank you for the reply taurus, yes I checked the burn and I also checked cd for defects at start-up.

What i have done now is downloaded from a different source but still get the same error code it has numbers but goes so fast it is hard to catch I remember the letters ACPI and error code Unable to load system description tables.

I have tried 2 different cd's on this both check well and seem to install well, if it makes it to my password,,then I give it password and after shows a cream colored screen or a complete black screen with the cursor which I can still move around on the screen, but it will not go further than this.

This one lone error is causing it not to boot Ubuntu,,if you have any ideas please post reply, meanwhile I will prowl around the forumns to see if the problem has occur before, but any ideas of what causing this plaese help.

---

### Post by floydv on 2009-01-16
Found something on here that worked for me and was able to boot,,

In Grub Select recovery mode

Drop to root shell prompt

type- sudo apt-get remove compiz
and enter

then type- sudo apt-get remove compiz-core
and enter

exit and resume normal boot

This worked for me, don't know what exactly it did or anything but after finding this in the forumns and trying it, it worked for me.

---

