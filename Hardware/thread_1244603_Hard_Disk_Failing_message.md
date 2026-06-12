---
title: "Hard Disk Failing message"
date: 2009-08-19
forum: Hardware
---

### Post by xnevermore on 2009-08-19
I keep getting a message box popup when logging in that reads, "A hard disk is failing. One or more hard disks report health problems. Click the icon to get more information". Should I be worried about this? Checking my disks with fsck reports no problems. Screenshot attached.

---

### Post by PatrickVogeli on 2009-08-19
The hard drive is probably reporting problems using the S.M.A.R.T. technology, which somehow can "predict" some hardware related problems in the HDD.. I don't know how accurate it is, but I'd think of getting a new hard drive. Since they don't cost that much nowadays and loosing the information can be a real pain..

You can also use the smartmontools to investigate further. I don't know how to use them, but man smartctl should give you a clue.

---

