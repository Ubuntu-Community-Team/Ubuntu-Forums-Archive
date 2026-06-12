---
title: "Asus EEE PC 1000HE power issues"
date: 2010-07-28
forum: Hardware
---

### Post by Dano_Austin on 2010-07-28
I loaded 10.04 on my Asus EEE PC 1000HE.  Everything works perfectly, except it will not run on battery.

It ran fine on battery using XP, and 7, however when I unplug the power while Ubuntu is running, it immediately turns off, like the battery is dead.

The battery is not dead..i can get 4 hours out of it on 7

Any ideas?  I searched Google and these forums, not finding an answer.

Thanks!

---

### Post by Dano_Austin on 2010-07-28
Forgot to mention I am running the Netbook version of Ubuntu.  Am going to download the full version and see how that is

---

### Post by Halzacar on 2010-07-28
Hmmm....I can't be of much help but i can say that i don't think its an actual bug in UNE as I ran UNE on my fiancee's 1000HE before i got my new netbook and I never had a battery problem...

---

### Post by Dano_Austin on 2010-07-29
> **Halzacar said:**
> Hmmm....I can't be of much help but i can say that i don't think its an actual bug in UNE as I ran UNE on my fiancee's 1000HE before i got my new netbook and I never had a battery problem...


Thanks for your response.  While I agree it seems to be an issue with my system, that doesn't explain why my battery works fine with XP and Windows 7.

Im going to try the desktop version of Ubuntu.  I am not to big on the netbook theme anyways.

---

### Post by P4man on 2010-07-29
Try this; press alt+f2 and enter
```

gconf-editor
```

Browse to
/apps/gnome-power-manager/general/use_time_for_policy

Set it.

---

