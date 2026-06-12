---
title: "Kernel panic....can't boot from anything"
date: 2009-02-27
forum: Hardware
---

### Post by Jeenyus on 2009-02-27
So today I was on my computer and I ran out to the liquor store and came back to find my computer (ubuntu 8.10 desktop edition) frozen.  This isn't the first time it happened so I just held the power button as usual and tried to turn it back on again.  When I attempted to boot into Ubutnu, i received a screen full of text with the last line reading "Kernel panic - not syncing: Attempted to kill init!"  Needless to say I was very confused, so I hard reset again and tried to boot into another kernel.... same results.  After another reboot I tried recovery mode on the original kernel and same results.  So then I figured I'd try to boot into my WinXP partition (I dual boot XP/8.10) and upon booting into XP I received a flash of the infamous "blue screen of death" and then the computer turns off instantly and I can't read any of the text.  So I am able to boot into any of my installed operating systems.

So then I grabbed my 8.10 install disk to boot into the Live CD and sure enough, same "kernel panic...." message!

So now I am absolutely clueless.  Any help is appreciated!

Thanks much,
Jeenyus

---

### Post by Jeenyus on 2009-03-02
Okay, so I've put working on this issue off for a couple of days and not I'm back at it.  Again no OS installation is booting, I'm still receiving the "kernel panic" message for ubuntu installations.  However I tried to run the memtest option at start up and I am receiving straight fails across the board.  Does this just mean bad memory? Or is it something much worse?

Thanks,
Jeenyus

---

### Post by deepclutch on 2009-03-02
do a "sudo dpkg-reconfigure linux-image-`uname -r`"(without quotes!) .Also ,check your /boot/grub/menu.lst for ubuntu entry being correct.and check your hardware -harddisks ,BIOS(enable support for all available harddisk controllers,graphics card-including proper driver installed).
--
next time ,boot with "acpi=off" parameter on the kernel line for Ubuntu in menu.lst and try.

---

### Post by Jeenyus on 2009-03-07
I found that my RAM was actually shotty. I managed to boot into XP Safe Mode and was able to run some memory tests to find the memory had failed (which concurs with results of the memtest86). I was then able to shut down properly to re-install my old memory for the time being until Crucial sends me a replacement.

Thanks,
Jeenyus

---

