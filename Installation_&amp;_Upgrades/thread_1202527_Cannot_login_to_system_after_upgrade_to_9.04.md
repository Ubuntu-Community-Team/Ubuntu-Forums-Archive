---
title: "Cannot login to system after upgrade to 9.04"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by dehcbad25 on 2009-07-02
I upgraded from 8.10 to 9.04 last week and since them I have been unable to login into the system. IT says athentication failed when I try to login.
However, if I login with a domain password it works.
The system has likewise open installed.
M guess is that my PAM authentication is messed up somehow. Unfortunately I did not add any of the domain accounts as part of the sudoers, so I am in a bind here.\
If I start the system in single user, I can get to the root shell, but I cannot change passwords either. The system responds
```
passwd: Authentication token manipulation error
passwd: password unchanged
```Of course, the system is not very usable this way :p
I use this at work, so I want to avoid losing the files. It is a MSI Wind PC, with Atom procesor, 2 Hard drives in RAID 1, and Ubuntu installed from a USB drive.
BTW, I am pretty happy the read speed that It has this NAS type of built.
From my installation notes the RAID is as follow
   ```
SCSI device A 931.51 GB ATA WDC WD1001FALS-0 1 and SCSI device B 931.51 GB ATA WDC WD1001FALS-0 1 are configured as RAID 1 at /dev/md0 mounted on /mnt/raidarr/public with a total space of 931.51 GB
```
I am thinking repairing PAM would fix the problem. I don't want to remove likewise yet since it is the only way I can login into the system.
I am not a linux guru, but I can defend myself with some googling. I also run a VM ubuntu machine at work as my main web intranet web server.

---

### Post by dehcbad25 on 2009-07-06
I guess no one has an answer?
I was able to connect thru the network to the samba shares and I copied the files that I needed. I am going to see if I can copy some of the etc and conf files that I modified the most so I don't have to do everything again and I am going to fresh install Ubuntu, so before doing this any suggestions would be greatly appreciated.

---

### Post by aLiEnTxC on 2009-07-06
U can try pam-auth-update --force, then u get the normal pam setup back.

---

### Post by dehcbad25 on 2009-07-14
Thanks for the suggestion. I tried it, but still does not work.
Since I had installed Ubuntu in a thumb drive, I changed the thumb drive and installed 9.04 from schratch and then mounted the RAID volume. This time also I did not use LVM in case I ever need to edit a file and the system does not boot. I wonder what broke the system. I made a lot of changes. Anyways, now I get to try again with likewise from scratch.

---

