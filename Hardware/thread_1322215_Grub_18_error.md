---
title: "Grub 18 error"
date: 2009-11-10
forum: Hardware
---

### Post by kamkar1 on 2009-11-10
Hi folks,
I am a newbie at Linux. Have installed Linux on 3 laptops at home. The gateway computer worked just fine for 3 months, yestrday I got Grub Error 18.
googled the issue and change BIOS form 
Large Disk Access Mode from "DOS" to "Other" and I got it to work.
 
Today, I got the same error and now it does not allow me to boot Ubuntu.
Any recommendation on how to repair?

---

### Post by RossDoughty on 2009-11-10
More information please, is there more than one OS on the disk? Have you tried changing your jumper settings on your HD to "Cable Select"? That worked for me when I had troubles with a system the other day :).

---

### Post by kamkar1 on 2009-11-13
Thank you for your response. I new at this forum and wondering if I posted correctly?

To answer your question ...
Gateway laptop computer with working copy of XP. Installed Ubuntu about 2 months ago (5g partition) to stop managing XP, malware and viruses my son was getting. I was using it for two months then I started getting the error 18. Changed BIOS setting LMBA from "DOS" to "OTHER" and I was able to get access. finally it stoped working. No access to either XP nor ubuntu.

I searched couple of ubuntu forums they were mostly pointing to new installations that had the same error 18. 
One of the forms was poiting to corrupted grub, the commands were ..
Sudo grub
root (hd followed by TAB key
root (hd0,4) pointed to partition of grub
setup

Nothing worked. I reinstalled ubuntu and got both operating systems back. However I would like to know what I did wrong. thank you jk

---

