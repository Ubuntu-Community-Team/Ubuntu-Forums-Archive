---
title: "Jaunty upgrade destroyed my partition tables"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by nashibuntu on 2009-06-05
I just upgraded to Jaunty. It was all going fine, but before it restarted I noticed a load of messages saying that it could not find the partition table for any of my partitions. When it restarted I got a message saying that my raid array was degraded. Indeed two of the raid pairs had been set up with only one partition rather than two and with names like md_d1 and md_d6 rather than md1 and md6. I had to stop these, reassemble and check them using mdadm. I also did an e2fsck on all of them. Everything appeared to be fine so I exited and let the system continue to boot.

While booting it still complained that it can't find the partition tables.

Ironically, I was only upgrading to Jaunty because a patch to the linux kernel that prevents my machine from going into kernel panic on boot became available today!

Attached are the outputs of:

sudo fdisk -lu
sudo sfdisk -d
cat /proc/mdstat

The sfdisk output shows correct partition tables for the individual partitions (sd...), but all the entries for the raided one (md...) are missing or incorrect.

The most annoying thing is that every time I reboot, my raid array is degraded and I have to re-assemble it before I can continue the boot process.

Can someone here help me to re-build my partition tables please? I think it should be possible to use the output of sfdisk -d, using info about:

sda1 or sdb1 for md0
sda5 or sdb5 for md1
sda6 or sdb6 for md2
sda7 or sdb7 for md3
sda8 or sdb8 for md4
sda9 or sdb9 for md5
sda10 or sdb10 for md6

but I'm no expert.

Also, could this be related to [bug 334278]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/334278"), which is supposed to have been fixed?

Thanks.

---

### Post by ronparent on 2009-06-05
Your partition tables are not destroyed. The main problem with 9.04 and raid is that the raid is not automatically activated and thus any raid drive mounted by fstab on boot will not be automatically mounted. Your experience will be typical of anyone booting on a raid! As you have found you can manually assemble and mount the raid drives.

I have reported it to launchpad as a problem with dmraid, but, from the experience of yourself and others it appears that it is a problem with mdadm also. Some people in the servers forum have apparently found work-arounds. My personal solution has been to drop back to 8.10 (after making a dedicated /home partition). The install of 8.10 over 9.04 (without formatting) had incidently left me loading with the new kernel! I have been using it without problem!

Your alternatives seem to be to adopt one of the work-arounds or reinstall 8.10. You might find help for the work around on the servers forum.

---

### Post by nashibuntu on 2009-06-06
ronparent. Thank you very much for your reply. I'll be looking into the workarounds, or maybe I'll just hope that I don't need to restart my server and there are no power cuts until it has been fixed.

It's sad that the situation really is as bad as I feared and I am really quite annoyed with Ubuntu. Surely the mdadm package should have been tested with Jaunty before release?

Given that this experience is typical of anyone using raid, I'd like to suggest to the Ubuntu people that
[LIST=1]
[*]a warning about this issue is placed on the [upgrade](https://help.ubuntu.com/community/JauntyUpgrades) or [release notes](http://www.ubuntu.com/getubuntu/releasenotes/904) pages, and
[*]a check for a RAID based system is introduced at the start of an upgrade with a warning and with an option to not do the upgrade.
[/LIST]

Thanks.

---

### Post by nashibuntu on 2009-06-06
It appears to be a known bug: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/366204](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/366204)

There are solutions provided on that thread. Here are the details of how I fixed it for anyone that's interested. My computer was crashing out into an initramfs shell on boot with a degraded raid array message. So, first I had to make the machine bootable:

[LIST]
[*]Check the status of my raid arrays
```
cat /proc/mdstat
```
[*]Stop any badly partitioned md arrays. Something like
```
mdadm --stop /dev/md...
```
[*]Reassemble the raid arrays correctly. Something like:
```
mdadm --assemble /dev/md... /dev/sda... /dev/sdb...
```
exit the shell and the computer should boot.
[/LIST]

Once booted, I needed to sort out my mdadm.conf AND update my initramfs:
[LIST]
[*]To update my mdadm.conf file with the correct info I ran:
```
sudo mdadm --examine --scan --config=mdadm.conf > mdadm.temp
```
I then removed the bad lines from /etc/mdadm/mdadm.conf and replaced them with the correct output of mdadm.temp. I left my DEVICE, MAILADDR etc. settings as is.
[*]The next step was crucial for me, since without out it, my mdadm.conf would apparently be ignored and the raid array would be reinitialised to its degraded state on boot. I ran
```
sudo update-initramfs -k `uname -r` -c -v
```
[/LIST]

I rebooted and everything was fine.

Cheers.

---

### Post by rmb3518 on 2009-08-27
I followed this to get my RAID mounted again, worked great.

[http://www.splatdot.com/2009/04/24/ubuntu-904-jaunty-jackalope-upgrade-notes](http://www.splatdot.com/2009/04/24/ubuntu-904-jaunty-jackalope-upgrade-notes)

---

