---
title: "Suspend lost, normal boot instead"
date: 2018-03-07
forum: Hardware
---

### Post by melser.anton on 2018-03-07
Hi,

I have an extremely annoying issue with 16.04 on my Dell XPS 13 2015 - suspend (either on lid close or manual suspend) gets "lost" - i.e., it is like I hard shutdown and it boots to grub with the session completely lost. It first started around the time meltdown appeared and I was playing around with the canonical testing ppa. At the time I accepted it as necessary but it continued after things went stable, and I simply couldn't work out what was going on. Then it magically stopped without me doing anything (intentionally anyway!), and happiness returned and showered flowers once again upon the world. After having a bit of trouble getting it set up in the first place (cf the issues other people have had with it not going to suspend and the screen just turning off), it worked flawlessly for many months. Then it just didn't any more...

Now, again without me doing anything intentionally, it has started failing again. And a shadow once more engulfed the land and imprisoned all the kittens :(. It doesn't appear to be kernel related - I have 4.13.0-36-generic, 4.13.0-32-generic and 4.4.0-116-generic installed and they all fail in the same way. I vaguely thought it might be firmware related as the linux-firmware package was updated from 1.157.16 to 1.157.17 around the time it started again but downgrading did nothing.

Can anyone point me in the direction of some logs I can look at to find out what might be causing the issue? Thanks!

---

### Post by melser.anton on 2018-03-07
Ok, I managed to get it working again - now I'd really like to understand what was going on! What did I do?

(I first tried `sudo systemctl suspend`, failed exactly the same as before, then)

$ sudo systemctl hibernate

Upon powering up again, it went to grub and I thought everything would boot as before... Nope - blank screen and no way to get control of the machine, so I do a hard (long press) poweroff using the power button. Then when it boots up I get some output very quickly printed out over the normal (Lubuntu) boot splash that disappeared quickly. After that, everything is working as expected.

My theory - at some point a suspend goes wrong and leaves some cruft somewhere that stops suspend being able to work properly. Until said cruft is cleaned, suspend/hibernate won't work. When said cruft is cleaned, everything works fine again, and somehow hard poweroff on a borked hibernate resume convinced the system to do the required cleaning.

Can someone confirm/infirm my theory? If so, does anyone know how we can clean up the suspend cruft without randomly trying suspend/hibernates and hard poweroff until it happens magically?

---

