---
title: "fsck fail on boot questions"
date: 2010-03-30
forum: Hardware
---

### Post by moody_mark on 2010-03-30
Hi All, I booted my regular machine today and it failed to boot complaining it was unable to mount the disc and threw me out to a root prompt. So I tried booting into the failsafe kernel and it gave me some more detailled messages from fsck.

Basically what I could deduce from the errors was that a file I had ftp-ed onto the machine yesterday was pointing to the same disc block as one of the gdm log files.

Fortunately I have a external USB with ubuntu installed so after making a note of which files were clashing, I booted from that and mounted the drive. I deleted one of the files (not the gdm log) and then unmounted to drive and run fsck against it choosing the "y" when prompted to fix. Now I can boot the machine normally off the internal hard drive.

I have some questions on this;

1. How could two files ever point to one disc block?
2. If I faced this error where would boot time fsck errors be written to?
3. Which logs would show any errors such as this so I could check before finding out on next boot I had a problem?

---

