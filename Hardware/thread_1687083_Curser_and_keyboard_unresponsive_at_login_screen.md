---
title: "Curser and keyboard unresponsive at login screen"
date: 2011-02-13
forum: Hardware
---

### Post by cidermonk3y on 2011-02-13
Hello all, got a bit of problem booting into ubuntu on my laptop.  What's happening is it seems to boot up fine, gets passed the ubuntu splash screen and gets to the login screen, (there are multiple users set up) but i have no cursor movement and no keyboard recognition (So basically it's just frozen with the cursor in the middle of the screen) :/

Specs - 

Ubuntu 10.04
HP Compaq 6735s
2gb ram
2gHz AMD Turion Processor

I've run through all the system diagnostic tests and nothing out of the ordinary happens,  so i'm stumped, i was hoping to be able to boot into a 'safe'mode but i can't see the option for it, can it be done?

Any help much appreciated.

---

### Post by cidermonk3y on 2011-02-16
I've done some research and found a similar problem - [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1447037](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1447037) 

The solution i thought could be turning off apic from the grub menu, so i hold <shift> get to the grub menu, select a kernal and hit 'e' to go to the editor.

I've tried adding noapic apic=off and such but to no avail,  i've tried putting it at the end of the kernal boot command line but still having the same issue.  Another thing i've noticed is i can't boot from the recovery mode, nothing happens, it's like it tries to boot up but just hangs doing some checks.

Does anyone think that the apic stuff is what's causing the problem or am i just putting it in the wrong place?

---

