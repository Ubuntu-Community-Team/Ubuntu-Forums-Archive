---
title: "dmraid ICH9 RAID 1 Problem"
date: 2009-09-18
forum: Hardware
---

### Post by Lepy on 2009-09-18
Hello fellow ubuntu users,

I've been having a wonderful time using ubuntu and learning linux on and off for over a year. Now that I've settled into my new place and painstakingly tailored my mythbuntu box to my exacting specifications, I need help fixing one problem that has kept me from using ubuntu as my OS of choice on my main desktop rig.

I have a RAID 1 on a P5k-Deluxe mobo (ICH9) that I created a while ago under XP to store backups, documents, media and the like; but upon activating dmraid, I get the output:
```
lepy@karmic:~$ sudo dmraid -ay
RAID set "isw_dfjeaigaha_Media" already active
ERROR: dos: partition address past end of RAID device
```

In gparted, both /dev/sdb and /dev/sdc show ntfs file systems with a warning, and /dev/mapper/isw_dfjeaigaha_Media shows up as unallocated space.

Upon searching for a solution, I came upon Launchpad Bug #395336: [https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/395336](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/395336)

It seems the M$ partitioner is to blame, not dmraid, and a simple fix would be to format and recreate the RAID under ubuntu; however, my 1tb RAID is approaching its upper limits and at the moment I don't want to buy another 1tb drive just to transfer the data and repartition.

I do want to have access to my RAID on ubuntu though, so I can leave Win7 behind for everything excepting gaming. So, can anyone suggest a way to successfully active the RAID while also retaining my data. Its kinda the whole reason I created the RAID in the first place?

---

### Post by Lepy on 2009-09-22
Am I out of luck?

---

### Post by Lepy on 2009-09-24
Bump

---

### Post by Lepy on 2009-09-28
I'll give it another try. 
Bump!

---

