---
title: "[SOLVED] Hard Drive fell - program to verify fully functioning?"
date: 2008-10-26
forum: Hardware
---

### Post by shaggy999 on 2008-10-26
I was doing some work on my computer and I had disconnected a hard drive and removed it from the chassis and set it on top of the motherboard. Then I forgot about it and titled the machine 90 degrees. The hard drive fell with a BANG from about 12" height. I have it plugged in via an external IDE -> USB adapter and it seems to be working fine. File system comes up and I copied a couple of large files. But I'm hoping I can find something that can verify that the drive works 100%. I would use the smartmontools package, but it doesn't work on drives connected over USB and I can't connect it internally because the power supply can't handle it (it shuts off after a few seconds if I plug in 2 drives). Anybody have any ideas?

---

### Post by teaker1s on 2008-10-26
in theory the heads would have been parked= no damage fsck may help or hard drive manufacturer normally have health checking tools

---

### Post by Lord Xeb on 2008-10-26
Just go in and check it with fsck. Also, pay attention to it if it starts making wierd noises

---

### Post by shaggy999 on 2008-10-28
Thanks for the tips. The drive appears to be working fine. I did run fsck and it came back ok. Then I did some partition re-sizing and a bunch of other stuff. I've been writing to it constantly for nearly 24 hours straight so I guess it's good. :)

---

