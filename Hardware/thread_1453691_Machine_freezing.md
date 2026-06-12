---
title: "Machine freezing"
date: 2010-04-13
forum: Hardware
---

### Post by Scruff343 on 2010-04-13
Hi I just put Ubuntu on my partners machine as they were Windows 7 and it kept blue screening on them so automatically Ububntu went on.

But now it freezes and sometimes the Caps Lock and Scroll Lock keys flash when it freezes.  The machine is basically used for World of Warcraft so today I sat on it doing other more taxing things and it didn't freeze.  Could this be a hardware problem or compatibility issue as I honestly don't know what to do is there any programs that can check the hardware of even give me a more detailed report of why it is doing this.

Please reply ASAP
Thanks :D

---

### Post by 2hot6ft2 on 2010-04-13
When the Caps Lock and Scroll Lock keys flash it's called kernel panic meaning something's wrong.
You could try booting into another kernel and see if it still happens.
You do have another kernel to choose in the grub menu right?
That's why everyone always says to keep at least the 2 most recent kernels. So you have another one to fall back too if the newest one has problems (like a kernel panic).

Yes, it could be a hardware problem or compatibility issue if you have any usb attachments try unplugging them and see if it still happens.
I've never had to resort to reading the system logs but there is
System > Administration > Log File Viewer
Just don't ask me which log to look at.
I guess the end of each would be the place to look after a freeze/crash.

That's about the best I can do for you.

---

### Post by Scruff343 on 2010-04-15
Ty anyhow :D

---

