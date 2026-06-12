---
title: "Ubuntu/Mint crashing/freezing at or before login screen"
date: 2018-04-13
forum: Hardware
---

### Post by jessthebear on 2018-04-13
[COLOR=#111111][FONT=Ubuntu]I am currently dual booting with Windows 10 (or trying to) on this laptop, and I have seen this problem on forums before, however no answer has provided a long term/permanent solution for me. I believe it is to do with my dual graphics (Intel on-board graphics and Nvidia GTX 960M) having some sort of conflict. I have tried booting with nomodeset and nouveua modeset both to 0 but it is quite temperamental if it works or not.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have had this problem with freezing or black screens on about 3 or 4 installations of different distros so I am certain it is a hardware conflict issue, however I am not intelligent enough to fix this on my own so please impart your wonderful Linux wisdom on me so I can actually use it! Happy to provide more details (specs, logs (if taught how)) on request![/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thank you in advance.

Edit: changed graphics card to what it actually is, not what I thought (and wished) it was.[/FONT][/COLOR]

---

### Post by QIII on 2018-04-13
Hello!

Which release of Ubuntu are you running?

---

### Post by jessthebear on 2018-04-13
Oops apologies I thought I posted that! 17.10, Also hi yourself! :)

Edit: Just wanted to provide a few more details as I have just tried launching again with a few different parameters to give you guys a better picture.

nvidia/nouveau.modeset=0 either at the end of the linux line or by deleting quiet splash and replacing it provides me the same result as launching normally (frozen login screen).
nomodeset at the end of the linux line starts showing me lots of "ok's" on boot and after trying user managed uid 121 for a while it then gets stuck on "Starting Load/Save RF Kill Switch" and will not get past that.
nomodeset/i915.modeset=0 instead of quiet splash goes through a similar process (though doesn't hang on user manager uid 121) but gets stuck on "Starting WPA Applicant".
Finally, i915.modeset=0 at the end of the linux line just stops doing anything after I press F10 to try and boot like that, no further things appear on screen.

I hope this provides you with a bit more insight into my issue/s, thank you for any replies in advance :)

---

