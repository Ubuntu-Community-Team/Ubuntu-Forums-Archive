---
title: "Grub installation has failed"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by slamelov on 2009-11-08
Hi

I'm tired of trying to install 9.10. I don't understand what's the problem. First, I was not able to upgrade from 9.04:
[http://ubuntuforums.org/showthread.php?t=1307780](http://ubuntuforums.org/showthread.php?t=1307780)
Of course it was not solved, and I had to make a fresh install. But it does not work.

After 94%, a message says: Grub installation has failed. Grub package can't be installed in /target/. And then, installation stops.

There is not any problem with 9.04, but I would like to upgrade to 9.10. May be it be impossible for me.

Regards

---

### Post by slamelov on 2009-11-08
It's strange, also, that Ubuntu 9.10 does not detect my 4 disks, but 9.04 does it. Could anyone explain me what I'm doing wrong?

---

### Post by slamelov on 2009-11-10
Any help, please?

---

### Post by darkod on 2009-11-10
If you just select the Try Ubuntu options first to see how 9.10 would run, what happens?

Does it go into desktop? Can you work on it? Are the drives in Places menu?

---

### Post by slamelov on 2009-11-10
> **darkod said:**
> If you just select the Try Ubuntu options first to see how 9.10 would run, what happens?

Does it go into desktop? Can you work on it? Are the drives in Places menu?

Yes, the Live CD works, but it does not detect all the disks.

---

### Post by darkod on 2009-11-10
Sorry, I am quite new to Ubuntu. I have no clue why it wouldn't see drives.

Have you read something about the IDE or AHCI mode of SATA drives? For windows SATA mode usually has to be set to IDE. Don't know if that can make problems for Ubuntu, it should work fine.

I have dual boot od Win7 and Karmic on my desktop with the SATA drive in IDE mode.

---

### Post by slamelov on 2009-11-10
The strange is that It works in 9.04. There is something new in 9.10 that changed grub or something.

---

### Post by darkod on 2009-11-10
Are all drives SATA?

Maybe it can see the ide drives but doesn't see you sata controller, incompatible version maybe. Just guessing here...

---

### Post by slamelov on 2009-11-10
Yes, all drives are Sata except DVD.

---

