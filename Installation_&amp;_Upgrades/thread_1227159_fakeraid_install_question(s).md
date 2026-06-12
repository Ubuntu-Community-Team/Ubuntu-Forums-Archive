---
title: "fakeraid install question(s)"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by sdlinux on 2009-07-30
I want to setup ubuntu 9.04 64 bit on a SATA Raid1 motherboard. Windows is already installed and the raid works. I followed the instructions at:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) I used the graphical installer on the live CD.

This is some of the output i got. 
> RAID set "pdc_ceddccceea" already active
RAID set "pdc_ceddccceea1" already active
RAID set "pdc_ceddccceea5" already active
RAID set "pdc_ceddccceea6" already active
RAID set "pdc_ceddccceea7" already active
RAID set "pdc_ceddccceea8" already activeSome of the commands I used.
```
sudo mount /dev/mapper/pdc_ceddccceea6 /target/
device (hd0) /dev/mapper/pdc_ceddccceea6
```1) should I have used hd0? Look at the output I got, I think this is an error?

> Unknown partition table signature
 (hd1,5)some more commands I did
```
root (hd1,5)
setup (hd1)
echo dm-raid4-5 >> /etc/initramfs-tools/modules
```Other Questions:
2) Why did I have to put dm-raid4-5 if I am using raid 1?

3) On the installation, it said it was going to make changes to each individual drive, even though I had made sure to select "do not use this drive" on all the partitions and I told it not to install grub. Could that have messed something up?

4)  What should I have put in the grub configuration so I can dual boot to windows? I put in the following since my windows is the first partition on the drive. Is it correct?
```
title                 Windows
rootnoverify (hd1,0)   # use the correct partition for Windows, of course
makeactive
chainloader +1
```
5) Finally, I rebooted and grub did not come up, It just booted straight to windows. What did I do wrong?

---

### Post by sdlinux on 2009-07-30
bump. Am I in the wrong forum?

---

### Post by dstew on 2009-07-30
No, it is OK to post RAID questions here. Since Ubuntu does not really support "FakeRAID", there are not a lot of success stories to share. Hopefully, one day, FakeRAID support will be made available.

[Here is a forum post]("http://www.linuxquestions.org/questions/linux-newbie-8/strange-partition-in-fakeraid-system-after-installing-windows-7-738061/") where TestDisk fixed the problem. It sounds similar to your problem. But, there is not much detail in the post.

---

