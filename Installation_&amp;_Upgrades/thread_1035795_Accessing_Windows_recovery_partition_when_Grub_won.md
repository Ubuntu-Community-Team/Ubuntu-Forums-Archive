---
title: "Accessing Windows recovery partition when Grub won't let you F11 it?"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by StarVoiceReason on 2009-01-10
Hi!  It's me again.  My earlier problem involving shrinking Vista down too far has expanded.  I used gparted and gave windows more space, but it refuses to see it.  Or rather, windows partition manager says windows has more space, but windows says it doesn't have any.  Anybody have a clue??
I can't use the recovery partition because grub cuts off any attempts to bring up the recovery function...  I press F11, it starts to open recovery manager...  and then Grub cuts it off.  And I can't make a recovery disc because recovery manager goes straight to an error box and shuts itself down.
HELP!!!
-SVR

---

### Post by kranny on 2009-01-10
> windows partition manager says windows has more space, but windows says it doesn't have any.
-SVR

I dint get you

---

### Post by Herman on 2009-01-10
> I can't use the recovery partition because grub cuts off any attempts to bring up the recovery function... I press F11, it starts to open recovery manager... and then Grub cuts it off. And I can't make a recovery disc because recovery manager goes straight to an error box and shuts itself down.
 It might be a good thing if you can't use your 'recovery' partition if you still want to keep Ubuntu. 
Different 'recovery' partitions work different ways, but some of them might wipe everything else off your computer and restore your computer to it's 'factory shipped state'. I'm not sure, but I would worry about that.

If you're sure you want to run the 'recovery' partition you should be able to chainload it from GRUB.
Just add another boot stanza like the one you already have for booting Windows, but specify the boot sector of the 'recovery' partition and it should boot.

Regards, Herman :)

---

