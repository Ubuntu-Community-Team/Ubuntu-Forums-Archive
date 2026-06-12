---
title: "[SOLVED] &amp;quot;extra&amp;quot; help to boot of DVD from grub"
date: 2008-11-21
forum: General Help
---

### Post by dmitrijledkov on 2008-11-21
I got IBM ThinkPad T30 for free as a present. It had Windows XP on it. I've burned Ibex Live CD onto DVD+R, popped it in, reboot, choose to boot of cd and it failed.

In windows I've ran the Wubi, and choise to get "extra" help booting of cd. That worked and I installed Ubuntu using up all hard drive.

Now Windows is gone, but I want to boot of that Live CD (burned onto DVD) again and I'm failing.

Is it possible to have boot of CD option in grub menu, cause that would be amazing. I have no clue how to do that though =( Please help.

I want to try a few live cd, and DVD+R is the only media I have lying around. (Maybe the DVD+R is the problem but I have no clue)

ps I really don't want to dual boot xp just to have that "extra" wubi help to boot of the CD's in the future.

---

### Post by dmitrijledkov on 2008-11-21
I've used later part of this wiki page [https://help.ubuntu.com/community/GrubHowto/BootFloppy]("https://help.ubuntu.com/community/GrubHowto/BootFloppy").

It was giving me error 15.

So I pressed "c" to go to console. I've typed
```

kernel      /boot/grub/memdisk
initrd      /boot/grub/sbm.bin
boot
```

and it worked. It got into the Super Boot Menu and I chose CD and it worked!!!!!! :guitar:

---

