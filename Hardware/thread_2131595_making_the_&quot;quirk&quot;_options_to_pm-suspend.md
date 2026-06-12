---
title: "making the &quot;quirk&quot; options to pm-suspend permanent?"
date: 2013-04-02
forum: Hardware
---

### Post by I_can_see_the_light on 2013-04-02
Hi,

I have a Radeon 5800 series video card on my computer and the open source drivers seem to work much better than the ones supplied by AMD in all cases but one: **resuming from suspend.**

With the binary blob the screen gets restored without problems, but with the gallium driver the monitor is giving me the message "Out of range". I found that putting the computer in suspend mode with the command below restores the video perfectly:
```
pm-suspend --quirk-vbe-post
```

My question now is how do I make that "quirk" a permanent setting when suspending?

---

### Post by José Serra on 2013-04-02
Hi, have you tried adding this option? --store-quirks-as-lkw

Regards.

---

### Post by I_can_see_the_light on 2013-04-02
Thank you, I'll look into that.

---

### Post by I_can_see_the_light on 2013-04-03
I tried the option **--store-quirks-as-lkw** but it didn't work reliably. Most likely it was because **--quirk-vbe-post** didn't solve the issue like I first thougt - apparently my computer can hibernate without issue and after hibernation the problem with suspending is gone as well :/

I found out that my brand new 12.04 install had lots of packages (xorg stuff) backported from 12.10 though, that's not really good for a release targeted towards workstations. I am positively sure that I did not install those packages myself. Fortunately enough I could install the old version of said packages and now suspend seem to be working fine again. 

I will mark the thread as solved since I won't be investigating this further.

---

