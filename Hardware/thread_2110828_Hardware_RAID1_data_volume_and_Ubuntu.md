---
title: "Hardware RAID1 data volume and Ubuntu"
date: 2013-01-31
forum: Hardware
---

### Post by geohei on 2013-01-31
Hi.

My motherboard (64bit, UEFI):
GA-Z77X-UD5H
Firmware: F14 (latest)

I use motherboard (hardware, Z77, NOT Marvell 88SE9172) RAID1 to mirror two identical HDDs. The created volume is exclusively used as data volume (as opposed to system volume). The filesystem is NTFS. The volume works fine with Windows 7, which is already installed on the system HDD. Windows 7 detects the volume as a single HDD (the way it should be).

I plan to use Ubuntu 12.10 Desktop on the same box (dual boot, installation on system HDD where Windows 7 is already installed).

Question ... will Ubuntu detect the volume also as one single HDD, and can I safely use (r/w) it without risk of data corruption?

Thanks,

---

### Post by geohei on 2013-01-31
Since data loss/corruption might be one of the consequences, I need to know if I can safely use Ubuntu with this RAID1 volumes.

Any ideas?

Or was the question not clear shall I rephrase?)?

Thanks,

---

### Post by geohei on 2013-02-02
After investiganting a bit further, I found this:

[http://askubuntu.com/questions/197561/installing-ubuntu-with-fake-raid-1](http://askubuntu.com/questions/197561/installing-ubuntu-with-fake-raid-1)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://www.kevinmccaughey.org/?p=182](http://www.kevinmccaughey.org/?p=182)

Reading all this, I believe that I cannot use the data on my FakeRAID1 within Ubuntu 12.10.

Can someone confirm this?

Thanks

---

### Post by ronparent on 2013-02-02
Lots of luck. I did get 12.10 working on a raid0 - in a round-about way. The 12.10 release note allude to problems with raid installations in that an alternate cd installation is not available! I did find a straight install fruitless and after many misspent hours decided to try something else. 

Bssically that was to install 12.10 to usb flash drive on computer with no active fakeRAID. I then installed dmraid to that same drive. I then created a ext4 partition on my raid as a target to copy the pen drive complete file system to. copied everything in the pendrive partition to the target partition, and edited the /etc/fstab to change the pendrive partition uuid to the target uuid - same for swap. You can update-grub on the pendrive to boot into your install. Once into it you can install-grub on the raid bssed system to also write the grub bootloader to the raid. That in a nutshell describes describes how I got my raid0 system up and running. 

I can't address raid1 data corruption - I haven't run on a raid1 but it is a potential problem with dmraid. The use of mdadm as in your third reference is likely unavailable to me because my system does not have an Intel chipset.

---

### Post by geohei on 2013-02-03
Thanks for your reply, but ... (1.) your setup deals with FakeRAID 0 (mine is FakeRAID 1) and (2.) yours is about _installing_ Ubuntu 12.10 on the FakeRAID (while I only use it as data HDD).

It's hard to believe that Ubuntu 12.10 is unable to properly mount a FakeRAID 1 if that array is simply used as data array.

I'm pretty sure there's a solution, but strangely, neither this forum, nor Google could lighten me up.

```
root@xxx:/dev/mapper# ls -l
total 0
crw------- 1 root root  10, 236 Feb  3 17:52 control
brw-rw---- 1 root disk 252,   1 Feb  3 17:52 isw_caaijgbdje_Data
lrwxrwxrwx 1 root root        7 Feb  3 17:52 isw_caaijgbdje_Data1 -> ../dm-0
lrwxrwxrwx 1 root root        7 Feb  3 17:52 isw_caaijgbdje_Data2 -> ../dm-2
```
What shall I do next?

---

### Post by ronparent on 2013-02-03
Try installing dmraid. Its installation should permit the raid partitions to be seen and be mountable. The dmraid program is not installed by default by Ubuntu if Ubuntu is installed to any partition other than on the raid.

---

### Post by geohei on 2013-02-03
I installed dmraid and ... it worked! Many thanks!!

The simple _installation_ of dmraid mounted the array (one single HDD i.s.o. 2 HDDs as before dmraid installation). I could read any write from Windows 7 and Ubuntu 12.10.

I didn't even _run_ the dmraid command - I just installed it. Is that the correct way to properly include a FakeRAID 1 into Ubuntu 12.10? Just an install, no dmraid command execution?

Since I have important data on this array, I need t know if it is perfectly safe to read and write the array without being afraid of data corruption.

Thanks!

---

### Post by ronparent on 2013-02-03
Congratulations. It is not necessary to run a dmraid command on boot since the raid is made active with the boot. 

There is apparently an issue with raid 1 in that apparently data corruption one drive can be replicated on the second. That is why it is generally recommended that a backup plan in effect is better assurance that your data will remain protected rather than depend on a raid 1 of any flavor. That said I know of no reason why it wouldn't be perfectly safe to read and write the array as you would to any other drive partition. Good luck.

---

### Post by geohei on 2013-02-05
> **ronparent said:**
> ...
There is apparently an issue with raid 1 in that apparently data corruption one drive can be replicated on the second.
...
Do you have further information on that one.
My Google skills didn't pop up anything.

Also ... is it normal that the array appears as removable drive in the Launcher (with the "Unmount" option on right-click)?
Nautilus also reports it as "Device" (as opposed to "Computer") with the eject button.

---

