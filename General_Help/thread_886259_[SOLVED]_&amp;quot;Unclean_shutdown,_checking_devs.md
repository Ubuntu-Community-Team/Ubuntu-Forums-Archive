---
title: "[SOLVED] &amp;quot;Unclean shutdown, checking /dev/sda2&amp;quot; gets stuck"
date: 2008-08-11
forum: General Help
---

### Post by KarateCowboy on 2008-08-11
Hi,

I was using ubuntu and it just froze.  Everything froze. Windows style. 

So after waiting five minutes for it to start working again I hit the power button and restarted.  It said "Unclean shutdown, checking /dev/sda2" and went through this check thing.

Well, it gets to 70% and then just sits there.  If press some keys, I'm not sure which combination it was, it brings me to this screen where it asks me for a root login or to press Control-D or something. The root log in does not work with my normal password.

Is there a way I can bypass this stupid check? Why is it not working? Geez. ready to kick my computer to pieces. It would be really nice to actually use this OS.

---

### Post by nazish on 2008-08-11
I too had this kind of problem, I dont exactly remember how I solved it but lets try it out.
 
Instead of booting into your normal ubuntu boot into the ubuntu recovery mode. Once you login run the following command
 
fsck /dev/sda2
 
then reboot into the normal ubuntu.

---

### Post by KarateCowboy on 2008-08-11
> **nazish said:**
> I too had this kind of problem, I dont exactly remember how I solved it but lets try it out.
 
Instead of booting into your normal ubuntu boot into the ubuntu recovery mode. Once you login run the following command
 
fsck /dev/sda2
 
then reboot into the normal ubuntu.
I just did that.  Well, I did fsck -v 

Basically did the same thing.  Linux is nicely self documented.  Unfortunately just not in the booting phases.

So,
1) Boot into recovery mode
2) sudo fsck -v or fsck -v /dev/sda2


This one is resolved.

---

