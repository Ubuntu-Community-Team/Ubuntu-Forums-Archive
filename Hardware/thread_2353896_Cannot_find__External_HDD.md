---
title: "Cannot find  External HDD"
date: 2017-02-26
forum: Hardware
---

### Post by crazychinesefarmboy on 2017-02-26
My Seagate Expansion drive has stopped responding. In windows the device was recognised but did not show up in device manager or in disk management. After booting ubuntu the HDD still will not read, the light is on and the device sounds and feels like it is operating. Please help after various fdisk and dmesg checks the HDD was only recognized once, I am not sure what to do next.

---

### Post by DuckHook on 2017-02-27
*Thread moved to **Hardware** as the more appropriate forum.*

If two different operating systems have problems connecting to your HDD, then the problem is highly likely to be hardware. Either your HDD is failing, you have a bad cable, a bad USB port, or a bad disk controller. The process of elimination is not difficult: do other storage media work on those ports? If so, then it's not likely to be the controller or the port. Is another HDD recognized on the same cable? If so, then it's not the cable.

When a drive physically fails, there's nothing much that software-based tools can do. You can try some of the data recovery tools here: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) but they all require a solid physical connection to the drive to do their work. If there is important data on it and it's not backed up, physical HDD recovery experts may be able to retrieve it.

---

