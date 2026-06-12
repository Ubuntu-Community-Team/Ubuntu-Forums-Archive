---
title: "This looks like a hard drive problem"
date: 2013-01-27
forum: Hardware
---

### Post by Lloydb39 on 2013-01-27
Xubuntu 11.10 on my Dell Inspiron 1150 laptop is telling me there is only .02 percent left on a 30 gig drive. Can't be. I have no video, about six photos and songs and a dozen documents. Only bare minimum of programs. Not long ago I had mucho space and it just disappeared overnight. Disk utility doesn't tell me much except that the disk is OK. Does anyone have a suggestion?

---

### Post by ibjsb4 on 2013-01-27
In terminal

```
df
```

Whats it say?

---

### Post by Lloydb39 on 2013-01-27
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             27606220  12316172  13887732  48% /
udev                    634948         4    634944   1% /dev
tmpfs                   256788       764    256024   1% /run
none                      5120         0      5120   0% /run/lock
none                    641960       172    641788   1% /run/shm

I had a typo. It is a 30 gig drive.
And now, suddenly, the little icon is saying "13.24/26.33 space left"
I did nothing, not even reboot, except use the df query
should i assume it is fixed?

---

### Post by ibjsb4 on 2013-01-27
If its no longer broke, we can't fix it  :)

Just post back if it happens again.

---

