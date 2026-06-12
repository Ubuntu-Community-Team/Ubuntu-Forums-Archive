---
title: "Unable to load 2.6.28-11 after upgrading to 9.04: GDM-related error?"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by khughitt on 2009-04-26
Hi all,

I recently upgraded a machine from 8.10 to 9.04, but after the upgrade finished and I restarted the machine, I could no longer boot up Xwindows. An error message relating to GDM is displayed along with an "ok" button:

"Server Authorization Directory (daemon/ServAuthDir) is set to /var/lib/gdm but is not owned by user root and group gdm. Please correct ownership or GDM configuration and restart GDM."

I tried opening a new shell (control + f2), logging in, and changeing the permissions, but the entire system was mounted as read-only so I could not.

I checked /etc/fstab and noticed that the partition is set to mount as read-only when an error occurs, so I'm guessing that is what is causing the problem, although I tried booting in recovery mode and running fsck with no luck.

I think the problem may be related to the fact that the parition uses the relatively new JFS filesystem format- I upgraded a similar machine that uses ext3 and did not run into any kind of problem like this. Anyone else using JFS run into any problems upgrading? I *am* able to boot into the system if I use the older kernel (2.6.27-11-generic), so the system isn't completely broken.

Has anyone else encountered similar problems? Any suggestions?

Any help would be greatly appreciated.
Thanks!

---

