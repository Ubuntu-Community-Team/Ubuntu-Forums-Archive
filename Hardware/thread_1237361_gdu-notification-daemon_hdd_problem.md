---
title: "gdu-notification-daemon hdd problem"
date: 2009-08-11
forum: Hardware
---

### Post by Michalxo on 2009-08-11
Hi all, 
I am having bug or some serious problem on my hdd. I am on 9.10 Alpha 3, but from today I am getting warning that my hdd may have bad sectors on it. 
It was scanned many times by that utility "Palimpsest Disk Utility 0.4" with no error found. I went into liveCD and ran badblocks on whole hdd with no errors on it either. 
Is it a bug? fsck.ext4 showed no errors too. Can anyone help me out with that? Thanks
Mich

---

### Post by Michalxo on 2009-08-11
bumpy bump :confused:

---

### Post by Michalxo on 2009-08-11
Help? :-/

---

### Post by Tilgovi on 2009-08-13
Same thing happened to me when I upgraded my Karmic install yesterday. I suspect it's a bug. Don't panic.

---

### Post by Michalxo on 2009-08-13
Already filled a bug here
 [https://bugs.launchpad.net/ubuntu/+bug/413064](https://bugs.launchpad.net/ubuntu/+bug/413064)

---

### Post by berarma on 2009-08-18
You should know these bad sectors are internally managed and replaced by the hdd hardware so no disk testing utility will find them except those using smartctl. I'm using Ubuntu 9.10 Alpha4 and it correctly warns me about a disk with too much defective sectors above the threshold, the only inconvenient is that I can't reset this notification and it appears every time I boot.

---

