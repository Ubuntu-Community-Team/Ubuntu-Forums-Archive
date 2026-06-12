---
title: "[SOLVED] VirtualBox + 2 Hard drives"
date: 2008-09-12
forum: General Help
---

### Post by FLCL on 2008-09-12
I have a quick question. I have virtual box running windows XP, but it does not take notice of my second drive i have plugged in. Is there a way for Virtual box to take notice of my secondary storage drive? Pleas help:confused:

Edit: Managed to find the folder on the second drive to make it shared. How do i access the shared folder? :S, and yeah i have guest additions installed.

---

### Post by quibbler on 2008-09-12
Open virtualbox...do not start or xp virtual drive.
Check on settings for the drive, go to shared folders
and add the drive or folder that you want.
Then start your xp.

Regards quibbler

---

### Post by FLCL on 2008-09-12
I did that, but i can't find the folder anywhere. Where is the shared folder located? I  says it's being shared, but i don't see it anywhere in xp

---

### Post by FLCL on 2008-09-12
It appears to be a bug :/, i tried one fix and it didnt, work. The shared path is not being read, any help?
Solved: I managed to get it working. For any who are interested, or happen to come across this thread, it was solved by removing the guest additions, and obtaining 6.0 version.

---

