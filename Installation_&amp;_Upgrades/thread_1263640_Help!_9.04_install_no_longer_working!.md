---
title: "Help! 9.04 install no longer working!"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by claus on 2009-09-11
Hi,

when trying to boot 9.04 today, I all of a sudden got an error message during boot-up (can't remember which one, but I got the impression that the system had been corrupted), so I used the live CD of 8.10 in order to install at least this version. During half of the installation I had the impression that the system had frozen, so I did a hardware reset (which was a mistake :-(. The result is that the live CD didn't boot up anymore, either. (Error: Can't read block at [hex value] - ad infinitum.) Now I have at least the live CD of 6.06 running, but the installation of 6.06 couldn't be completed for some reason, either (the installer quit).

Does anybody have a hint what I can do to get my system up and running again?   All of the partitions were reformatted, with the exception of **/home**, which is at **/dev/sda8**, and which I have been able to mount.

TIA,

Claus

---

### Post by mikewhatever on 2009-09-12
Could be a hardware problem. Anyway, without the error messages, it's really just guesswork.

---

### Post by claus on 2009-09-14
Hi,

thanks for your reply. The error message I have been getting when trying to boot the 8.10 live CD was
> 853.70881] SQASHFS error: Unable to read page block [hex value]

An answer on Launchpad to a similar problem says:

> Your CD/DVD Image is corrupt, try downloading it again and burn it

TIA,

Claus

---

### Post by claus on 2009-09-15
Hi again,

meanwhile I burnt a new 9.04 image, but the error persists. I found two threads on this, though, and the error

> 'IO APIC resource could not be allocated ...'

seems indeed to be hardware-related.

For more, see [IO APIC Resources?]("http://ubuntuforums.org/showthread.php?t=1181022"), [Just installed Jaunty ...]("http://ubuntuforums.org/showthread.php?t=1181067"), and [ MP-BIOS BUG 8254 ...]("http://www.linuxquestions.org/questions/linux-hardware-18/mp-bios-bug-8254-timer-not-connected-use-noapic-option-to-boot-591891/").

I'm going to try some of the options suggested in those threads.

Claus

---

