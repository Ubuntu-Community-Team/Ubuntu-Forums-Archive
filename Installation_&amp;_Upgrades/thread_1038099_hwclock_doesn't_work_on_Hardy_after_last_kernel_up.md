---
title: "hwclock doesn't work on Hardy after last kernel update"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by afilonov on 2009-01-12
hwclock stopped working after kernel (linux-image-386) was upgraded to version 2.6.24.23.25. Same problem on Thinkpad t41 and System76 Gazelle Performance Black. I didn't update kernel on desktop yet, and hwclock is working fine there. Symptoms:

hwclock --show
Cannot access the Hardware Clock via any known method.
Use the --debug option to see the details of our search for an access method.

hwclock --show --directisa
Mon 12 Jan 2009 11:48:10 AM CST  -0.752704 seconds

I had similar problems initially after upgrading from Dapper to Hardy, then some update fixed this problem. Now it's back again. Also, update reset System76 laptop BIOS clock to default.

Is there anybody else with this problem? I'm thinking of submitting a bug.

---

### Post by kranny on 2009-01-12
Post the o/p of 
```
hwclock --debug 
```
and are you sure that this is happening after a kernel update

---

### Post by afilonov on 2009-01-12
hwclock --debug
hwclock from util-linux-ng 2.13.1
hwclock: Open of /dev/rtc failed, errno=16: Device or resource busy.
No usable clock interface found.
Cannot access the Hardware Clock via any known method.



I am sure it's happening after kernel update. Of course, there were about 20 packages updated in that batch, including ntp. So it might be ntp problem as well. But hwclock is still working on desktop without those updates.

---

### Post by afilonov on 2009-01-17
Additional info: after updating desktop today, same problem, hwclock doesn't work. Desktop model is Dell PowerEdge 400SC. Strangely enough, no problem with older machines at work. Updated 4 of them, no problems.

---

### Post by afilonov on 2009-01-19
This is a return of the old bug 59596: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/59596](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/59596). All symptoms are the same. If you stop timidity, hwclock works just fine. I think it might be time to file a new bug.

---

### Post by afilonov on 2009-02-04
Filed new bug on this issue:

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/325518](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/325518)

---

### Post by afilonov on 2011-03-05
Marking as solved, upgraded all but one computer to 10.04, don't have any problem now.

---

