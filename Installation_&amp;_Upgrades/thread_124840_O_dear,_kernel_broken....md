---
title: "O dear, kernel broken..."
date: 2006-02-02
forum: Installation &amp; Upgrades
---

### Post by christhemonkey on 2006-02-02
I was recompiling myself a new kernel to enable preemption [http://ubuntustudio.com/wiki/index.php/Enabling_Pre-Emption_in_Breezy]("http://ubuntustudio.com/wiki/index.php/Enabling_Pre-Emption_in_Breezy")
When i first booted into my kernel, it said:

Segmentation fault
Segmentation fault
Segmentation fault
(and then again 7 times!)

then it says a lot of stuff about modprobe usage, then leaves me with some ASH thing, like a very basic prompt.

When i reboot into my normal 2.6.12 kernel it does the same now! Help!

Luckily i still have my 2.6.10 kernel installed so can boot into that, but still help appreciated!

Do i have to recompile my kernel? Do i have to stick with my .10 version?
Anyone?

---

### Post by fourchannel on 2006-02-02
i'm not sure how to get it to work right. But you might try this...

go into Synaptic and search for 'kernel'. it's going to be called linux-image-something find the 2.6.12 and select "completely remove" and hit apply. then go back and reinstall the 2.6.12. bout the only thing I can think of right now.

there might also be a command you can run, but i'm not so sure what it will do.

```
sudo dpkg-reconfigure linux-image-2.6.12-9-386
``` or whatever the package is called.

good luck, =D

---

### Post by christhemonkey on 2006-02-02
Cheers!

---

