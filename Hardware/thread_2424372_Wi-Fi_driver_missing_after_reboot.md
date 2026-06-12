---
title: "Wi-Fi driver missing after reboot"
date: 2019-08-07
forum: Hardware
---

### Post by subpar-user-1000 on 2019-08-07
I have a TP Link TL-WN822N wifi adapter and had the RTL8192EU driver installed and working well.
Today, I had to power my computer down (not gracefully) and when it came back up the driver appears to be gone.
I tried running through the steps to reinstall it, but I'm getting some weird errors there as well.

Maybe I'm missing something - could it still be there but "hidden" somehow? I do not see it in /lib/modules and lsmod doesn't show it.
Its weird that the computer won't even auto-detect the wifi card as it did previously.

Ubuntu 18.04

Any suggestions? Thanks!

---

### Post by Autodave on 2019-08-07
Is this a laptop?  If so, can you remove the battery easily?  If so, disconnect all cables and power brick. Remove battery. Wait at least 5 minutes and reconnect everything and power up and see if it is working.

---

### Post by subpar-user-1000 on 2019-08-07
It is a desktop.

---

### Post by subpar-user-1000 on 2019-08-07
So I must have had an older version of the driver or something. I had to edit a couple of the ".c" files and then it installed correctly. Would still be curious to know why everything disappeared in the first place?

---

