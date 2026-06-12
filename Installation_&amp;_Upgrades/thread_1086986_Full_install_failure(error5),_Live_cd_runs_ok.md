---
title: "Full install failure(error5), Live cd runs ok"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by mannshands on 2009-03-04
Hi all.
Tried to install several dists. Ended up with lots of partitions but nothing installed though the Live versions worked. Some showed grub error 5. Tried Grub Superdisc without success. Have settled on Ubuntu 8.1. Live cd is running. Tried to install using full disc option to clear out old partitions leftover from Mintlinux, OSLinux, Fedora and Zenwalk (looked primitive,it froze during format).
   So now I get (Errno 5)input/output error. Burned 2 discs at 2X on KCK DVD-R, using VSO Copy to DVD for one, and Power ISO for other. DVD player works ok. In cold room.  Been to lots of advice forums. Nothing seems to apply to me.
  BTW:Is a Sony Vaio vgn-ar61m that had HD erased by owners son by mistake trying to uninstall Vista. Can open Bios but looks ok.
  Whats next to try?
THX

---

### Post by theozzlives on 2009-03-04
Try partitioning, this worked on one of mine cause the disk was to big for the BIOS. Go to manual and delete all partitions and make new ones as follows:

1. root, ext3 (/): 10-20 GB depending on the size of your disk (10240-20480 MB)
2. swap twice the size of your RAM (extended)
3. /home, ext3: all the rest of the space

See if that helps.

---

### Post by mannshands on 2009-03-05
Linux just aint ready for me yet. Give it a few more years. New kernel in recent dists solves some probs, but still requires too much tweeking to install and add progs. 

As for my solution...new HD and WIN2000. Old school:popcorn:, but productive!!!
Thanks for help...:P

---

