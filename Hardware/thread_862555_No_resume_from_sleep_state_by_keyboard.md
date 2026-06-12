---
title: "No resume from sleep state by keyboard"
date: 2008-07-17
forum: Hardware
---

### Post by mbreman on 2008-07-17
Hello,

I have the following problem:

My system can not resume from a sleep state by pressing a key on my keyboard. The system does not wakes up. If I press the power button on the case the system does wake-up fine.
Before the system is back from the sleep state I get a message on the terminal like "keyboard activation failed". The keyboard does work fine after resuming from the sleep state.

If I look in the messages file there is a entry saying: "i8042: kbd activation failed"

I am running Hardy amd64 bits with kernel 2.6.24-19-generic. In the BIOS settings I have enabled the spacebar key for resuming from sleep state.

I have tried a PS/2 and a USB keyboard, but both have the same problem.

Anyone any ideas?

Regards,

-Mark-

---

### Post by mbreman on 2008-07-17
HHmmmm.... I think I found the answer in this post [http://ubuntuforums.org/showthread.php?t=814939](http://ubuntuforums.org/showthread.php?t=814939)

Looks like it's solved!

---

