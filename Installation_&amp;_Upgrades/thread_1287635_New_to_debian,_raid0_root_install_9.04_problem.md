---
title: "New to debian, raid0 root install 9.04 problem"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by oshunluvr on 2009-10-10
I'm a fairly experienced linux user and have done the below with many other distros. However, I am coming over from openSUSE and this is my first attempt at a debian based distro so there's a learning curve involved. Here's my situation:

4 sata hard drives, containing 4 different RAID0 partitions of various sizes. All clean and created with mdadm a year ago. No issues with any of the hardware.

I have 2 RAID0 devices I use as root partitions ( "/" ) for installs and two non-raid partition for use as "/boot? for these installs. I have successfully done this procedure with four other distros to install root to raid.

1. Boot liveCD
2. Install mdadm
3. Assemble arrays
4. Install OS to /boot partition and to / (RAID0) partition
5. Reboot and good to go.

Obviously, this method does not work with kubuntu jaunty. I spent the last six hours reading posts on this topic and most were regarding other issues (GRUB, dual booting, hardware or BIOS setup "fake" RAID). Many references to [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) but frankly this post isn't well written and jumps from issue to issue with very little real information about software raid - non of which helped me.

Here's what I've tried so far:
1. Steps above with kubuntu jaunty results in boot error "device /dev/md5 does not exist".
2. Figured out mdadm is not installed by default nor enabled in initramfs.
3. Did a side-by install to a non-RAID partition, installed mdadm, rebuilt initrd with mdadm enabled and then manually copied mdadm files from install to RAID partition and rebooted to RAID.
4. This resulted in a similar error at boot time, but when dumped to the command line busybox or initramfs command line or whatever you guys call it) the error still said /dev/md5 did not exist, but a quick "cat /proc/mdstat" showed all 4 RAID partitons up and running.

Its seems I'm close, but RAID isn't loading soon enough in the boot sequence to work.

What to try next???

---

### Post by lptr on 2009-10-11
Three years ago I had to do with fakeRAID, too. As far as I can remember the driver needs to get moved into kernel image that is loaded during boot. Note: I am not up to the current. Your statement seems to me, that the fakeRAID driver is not loaded during boot time. This means a) it could be, there is no driver support for RAID chipset on your mainboard at all or b) the driver support is there, but some configs need to get changed. I tend to believe it will be first, because this driver (at least in my case) was a specialised one that maybe is only directly available from fakeRAID controller manufacturer.

Just in case you did not think about it: Using a RAID usually means that you need to have more data security. On the other hand some users may expect higher performance - but this will work only with some scenarios. For later case it may be far better to buy high performance drives, maybe SSD drives with nearly no latency times. Of course this is much more expensive. But I believe you went through this already and you are trying to gain more security for your data.

So: When I tested with fakeRAID I found this is a pretty worse solution. I hope that you having your exact same mainboard on stock *at least* a second time, so in case of a controller break/failure you can access your data on the disks? I found - that time I was doing this testings - that SoftRAID is the far better approach. In both cases Soft and FakeRAID the main CPU does the work. The controller does barely nothing. 

If you need to have REAL high availability you need to have one of those pretty expensive controllers that doing all in hardware. If you are doing this, you will find a 'transparent' harddrive. The OS sees only the drive(s) that the RAID controller wants to get seen. Compared to this fakeRAID stuff where Linux sees several seperated drives. Even in this case you should have at least another controller handy to have a replacement in case of failure. Otherwise you having 100% data loss because failures usually appear several years after machine has been set up and then there is no option to get the same controller another time. Thinking of this...

regards,

rob*

---

### Post by oshunluvr on 2009-10-11
Thanks for your response but I am not using "fake" raid - which I believe refers to hardware based firmware or software controlled raid. 100's of posts here show that it is difficult to set up - if you can set it up at all. And as you mention - it's too hardware dependent. True hardware raid is ridiculously expensive, has the same hardware dependency issue, and from what I read is less reliable than linux software raid. 

I am using straight linux-only mdadm software raid. 

As I stated in my OP, the procedure I attempted works with Mandriva, Fedora, openSUSE, BlueWhite64 and others so clearly there is something "missing" from the (k)ubuntu installer to allow this to work. I'm just too new to the debian based Ubuntu world to know exactly what steps to take to fix this.

As far as your comments re: data loss - I backup.

---

