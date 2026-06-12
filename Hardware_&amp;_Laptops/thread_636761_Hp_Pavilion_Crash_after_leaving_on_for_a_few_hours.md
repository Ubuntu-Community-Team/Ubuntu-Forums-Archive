---
title: "Hp Pavilion Crash after leaving on for a few hours"
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by pchaffey on 2007-12-10
Hi,

I have an HP Pavilion dv6244eu (AMD64) which has Kubuntu 7.10 installed.

Everything is working well including some of the more strange hardware (wireless, webcam, IR remote !!), but when I leave the laptop on for a few hours (eg. over night) then the machine crashes with a black screen, and no keyboard access.

My first question is where do I look for some sort of Log of what actually whet wrong ?

After a powerdown and powerup, the log messages in dmesg look fine.

Could this have something to do with the machine trying to go into standby ?

I have added the following to the boot parameters in Grub:

noapic nolapic noirq nosmp

which switches most things off.....

Regards, Paul.

---

### Post by ajgreeny on 2007-12-10
This could well be down to the power saving settings, when the machine goes into standby or hibernates after a set time.  Try putting the machine in either standby or hibernation manually and you may find exactly the same thing, ie. you can't get back to a working system.  If that is the case, simply set the power saving to not standby or hibernate until ubuntu supports it better for your laptop.

---

### Post by pchaffey on 2007-12-11
Hi,

sorry for the simple question: but where do I setup power saving policies in Kubuntu 7.10 ?

I cannot find anything under "system settings"

Regards......

---

### Post by ajgreeny on 2007-12-11
Sorry, don't use kde so can't help.

---

