---
title: "SOLUTION to Aspire 5050 &quot;No Sound&quot; problem"
date: 2009-05-20
forum: Hardware
---

### Post by jungleexplorer on 2009-05-20
After trying many other solutions to this problem I found one that works. Here it is.

Open the Terminal and type:
**sudo gedit /etc/modprobe.d/alsa-base**

Then modify the following line :
**options snd-hda-intel**
so that it looks like :
**options snd-hda-intel model=acer-aspire**
the reboot and test if sound works.

If the line "options snd-hda-intel" does not exisit, simple add "options snd-hda-intel model=acer-aspire" the the list.  Save and reboot.  That should do the trick.

---

### Post by 100turion on 2009-09-16
I registered to the forum just to say: THANKS!

After 3hours of headaches this worked.

One minor detail, I has to use the command:

[B]sudo gedit /etc/modprobe.d/alsa-base.config

[/B]the missing ".config" part was opening a blank document.

---

### Post by jungleexplorer on 2009-09-29
Thanks for letting us know.  Good Luck!

---

