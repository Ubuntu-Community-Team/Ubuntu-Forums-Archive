---
title: "access rights on second hard drive"
date: 2020-04-05
forum: Hardware
---

### Post by george33 on 2020-04-05
Have desktop pc with a main harddrive of 500gig, running Ubuntu 14.04 tried upgrading to 18 but a hardware bug (reported) prevented it. my question however is about adding a second drive, i want to add a 1.5tb drive to hold media. have don so successfully and drive picked up fine.
have no root access i do not have write access therefore can not load any media files. So how do I get the required access rights to make and use folders on this drive?

thanks in advance

George

---

### Post by oldfred on 2020-04-05
Are you using fstab to mount partition or manually mount each time you want it?
Better to use fstab if internal drive.

What format is drive?
Post this:
sudo parted -l

You need to update or reinstall a current version of Ubuntu. You cannot update 14.04 anymore as it is EOL - end of life.

---

