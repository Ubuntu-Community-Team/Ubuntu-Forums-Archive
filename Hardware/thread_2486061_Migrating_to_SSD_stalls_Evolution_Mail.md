---
title: "Migrating to SSD stalls Evolution Mail"
date: 2023-04-18
forum: Hardware
---

### Post by gdesilva on 2023-04-18
Hi, I am running Ubuntu Studio 22.04 in Ubuntu Mate Desktop Environment and have my /home in a separate partition. Evolution Mail used to work perfectly OK until I moved the entire / partition to a separate Crucial SSD in the hope of speeding up the boot process and application response times.

This provided me with a noticeable response time improvement except that when I start Evolution Mail or when I come back mail after doing something, Evolution stalls for about 30 seconds. After this it works OK.

Initially, I set up the fstab so that the mount command includes the discard option. However, when I read the instructions on Crucial website I found a recommendation not to use the discard option as it does continuous cleanups which is likely to shorten the lifespan of the disk. Their recommendation was to remove the disacrd opton from fstab and to run a weekly cron job to run fstrim.

This appears to cause the Evolution Mail issue - so far, I have not noticed any other application behaving this way. I guess the reason may be only Evolution maintains a database and this may be causing write delays on the SSD. However, my Evolution Mail files reside in /home which is on a normal hard disk.

If anyone has any suggestions on how to overcome this issue it will be greatly appreciated.

Thanks.

---

