---
title: "Testing Ubuntu 10.04 destroyed my OSX bootloader"
date: 2010-04-30
forum: Hardware
---

### Post by tomislav7 on 2010-04-30
Hello everyone,
I have tried out today the new release of Ubuntu on my MacBook (late 2009). When leaving the Live-CD, the system asked me, as usual, to remove the CD and close the drive. I did as I was told, pressed enter, but nothing happened. So I waited for 5 minutes, then I pressed the Powerdown button. The strange thing is now: when I turn on my macbook again, it keeps telling me that there is no bootable device, and I have to insert one. The usual mac osx bootloader seems to be destroyed.
I don't have very much experience with the boot system of a macbook, although I have it only since a month, so I need your help!! How do I restore the osx bootloader? 
And, anyway, I ask myself: how could this happen? I didn't install anything, only testing the Ubuntu! Is this enough to destroy the bootloader?
greetings
tom

---

### Post by wheredidrealitygo on 2010-04-30
You need to take the OS X dvd you got with the machine (assuming this is was brand new when you bought it, if it's second hand you should still have gotten the dvd), the install dvd, not the application dvd.

Load it by holding down either the option key or the 'c' key when booting, and then choose 'startup disk' from the utilities/tools menu (i forget which it is offhand), and choose to boot off the installed OS X partition. when you're booted into the OS go into system preferences, startup disk, make sure the OS X partition is selected and reboot, that should re-bless your EFI partition and restore the bootloader. may have to do this more than once.

let me know how you make out.

---

### Post by tomislav7 on 2010-05-01
thanks for the answer, 
it turned out to be weird, though. At first, as I forgot to mention, I have no osx CD, because it's left in my other home, quite 9 hours by train from here.
However, I inserted the UBCD, I thought maybe I could somehow boot osx and installing the bootloader from there would be easy. Whatever, when I tried to boot, it didn't work out at all, the loader just stopped and I had to restart. 
Now I realised, that there is no way to put the CD out of my mac, because the button only works in osx, so the UBCD was captured in my computer! That's really an awkward feeling! :)
I tried a CDROM-Test in the Menu of UBCD and thought, maybe there was an option to eject any CD from the Computer. I did this, had no idea what was going on, only saw thousands of menus and strange lights, I dropped to a shell somehow and wrote: reboot. that's all I did.
Suddenly, like from the hand of God, my UBCD was spit out of my mac, after 5 hours in prison! Then something else happened (it was a thunderstorm at that time, maybe that's the reason) osx started again, like nothing had happened before!! The bootloader seemed somehow reinstalled! :confused: 
I know this sounds weird and there's no proper explanation at all, it could've also been the sushi I was eating :)
But anyway, the system works as usual and the problem is solved, thank god! (who else)

greetings
tom

---

