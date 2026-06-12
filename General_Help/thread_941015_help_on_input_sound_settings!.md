---
title: "help on input sound settings!"
date: 2008-10-07
forum: General Help
---

### Post by ieBrazil on 2008-10-07
Hi.

I've got Ubuntu Hardy Heron and it is, now, in almost perfect conditions. My laptop is an Acer, travelmate 2480 (Celeron, 420). I have RealTeck thing...

My input just do not work. I click on Sound Recorder but it appears a message saying my capture settings are not valid etc. I have changed everything possible and impossible there to get it fixed. But got nothing...

What do I have to do?

Thank you in advance, anyway.




ieBrazil

---

### Post by DagMan on 2008-10-07
you can try setting a paramater to the sound module and see if you can get it to work.
Try editing /etc/modprobe.d/alsa-base
and putting at the bottom of the file

```
options snd-hda-intel model=auto
```
and see if it works after a reboot.  Test it by using the capture device and not just the gui test thing.
other values that might work if the above doesn't, and trying only one at a time, are
options snd-hda-intel model=toshiba
and
options snd-hda-intel model=acer

I have an acer and using toshiba was the magic bullet.

---

### Post by ieBrazil on 2008-10-08
> **DagMan said:**
> you can try setting a paramater to the sound module and see if you can get it to work.
Try editing /etc/modprobe.d/alsa-base
and putting at the bottom of the file

```
options snd-hda-intel model=auto
```
and see if it works after a reboot.  Test it by using the capture device and not just the gui test thing.
other values that might work if the above doesn't, and trying only one at a time, are
options snd-hda-intel model=toshiba
and
options snd-hda-intel model=acer

I have an acer and using toshiba was the magic bullet.

Do you mean typing in that code in a terminal? and if one does not work, trying another? Is this it? I'll do it... but now I am using xp... Tnx!

---

