---
title: "RAID 5 array mdadm add no response"
date: 2013-06-11
forum: Hardware
---

### Post by chunky56 on 2013-06-11
On ubuntu server, I have a software RAID 5 array, four 2TB drives. One of the drives died, I sent it in and got a replacement. I put the replacement in my server, used an sfdisk command to set the partition table to the same as the other drives. I then tried to add this new drive to the array using the command:


```
sudo mdadm --manage /dev/md127 --add /dev/sdd1
```
Where md127 is the array name and sdd1 is the only partition on the new hard drive. However, when running this command, there is no response. I check /proc/mdstat to see if the array is resyncing and it does not seem to be doing anything. What am I doing wrong?

---

### Post by SaturnusDJ on 2013-06-11
More information is needed.

Can you add --verbose to the command and see what happens?
Also post the relevant entries from the syslog.

Also post the output of:
```
mdadm --detail /dev/md127
```
And:
```
mdadm --examine /dev/sd[a-d]1
```

---

### Post by chunky56 on 2013-06-12
Hey SaturnusDJ,

Strangely enough, I turned it on and now it seems to be recovering using the spare. I don't know why it didn't do this before. I will monitor it and let you know if I hit a snag later. Thanks for your help.

---

